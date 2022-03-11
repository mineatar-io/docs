---
description: A list of skin component coordinates and the Mojang API.
---

# 🎯 Skin Components

## Mojang API

Mojang provides a very simple JSON API for retrieving information about any player in their database. The response format is very straightforward, but the status codes can be confusing and sometimes not match what was actually returned. Please read this documentation carefully to understand how to interact with their API.

### 1. Username to UUID Lookup

If you already have the UUID of the player, you can go ahead and skin this step. This request is made to convert a player's username into a UUID, a unique string of characters identifying a specific player regardless of how many times they have changed their username.

{% swagger method="get" path="/users/profiles/minecraft/:username" baseUrl="https://api.mojang.com" summary="Retrieve UUID by Username" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="username" required="true" %}
The username of the player (case-insensitive)
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="The player was successfully found" %}
```json
{
    "name": "PassTheMayo",
    "id": "85e5f06eff894c118050329e8fdc29de"
}
```
{% endswagger-response %}

{% swagger-response status="204: No Content" description="The player was not found" %}

{% endswagger-response %}
{% endswagger %}

### 2. Retrieve Player Profile

By using the UUID from response in the `id` field in the request made above, you can now retrieve the profile information for the player by making another request to their session server. A UUID with or without dashes will still yield the same result.

{% swagger method="get" path="/session/minecraft/profile/:uuid" baseUrl="https://sessionserver.mojang.com" summary="Retrieve Profile by UUID" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="uuid" required="true" %}
The UUID of the player
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="The profile information was found" %}
```javascript
{
    "id": "85e5f06eff894c118050329e8fdc29de",
    "name": "PassTheMayo",
    "properties": [
        {
            "name": "textures",
            "value": "ewogICJ0aW1lc3RhbXAiIDogMTY0NzAyOTA2ODMzMCwKICAicHJvZmlsZUlkIiA6ICI4NWU1ZjA2ZWZmODk0YzExODA1MDMyOWU4ZmRjMjlkZSIsCiAgInByb2ZpbGVOYW1lIiA6ICJQYXNzVGhlTWF5byIsCiAgInRleHR1cmVzIiA6IHsKICAgICJTS0lOIiA6IHsKICAgICAgInVybCIgOiAiaHR0cDovL3RleHR1cmVzLm1pbmVjcmFmdC5uZXQvdGV4dHVyZS9iMWVhODNjODBmYWE2ZTEwYjlkNGYwODc1NWFkNmNmNTU5YTEyNTdjOGUwMDQwMDFiNGEzNzY4OGFkODBmNWIyIgogICAgfQogIH0KfQ=="
        }
    ]
}
```
{% endswagger-response %}

{% swagger-response status="204: No Content" description="The profile information was not found" %}

{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="Invalid UUID" %}
This means that you made a mistake and likely used the player's username instead of a UUID. Make sure the provided UUID is valid.

```javascript
{
    "path": "/session/minecraft/profile/PassTheMayo",
    "errorMessage": "Not a valid UUID: PassTheMayo",
    "developerMessage": "Not a valid UUID: PassTheMayo"
}
```
{% endswagger-response %}
{% endswagger %}

### 3. Finding Texture Value

The response value from the request made above contains a `properties` value, which is an array of objects. You will need to filter through the code above to find which object has the `name` property set to `"textures"`. It is not a good idea to just select the first value in the array because it may change at any time in the future. Here is some sample code on how to find the correct value:

```python
value = ""

for property in response.properties:
    if property.name != "textures":
        continue
    
    value = property.value

if len(value) < 1:
    raise Exception("'textures' property was not found in response")
```

All player lookups using this method should contain a textures property. If the player does not contain a textures property for some odd reason, you should instead use the default regular (Steve) skin. The contents of the `value` variable is Base64-encoded (standard encoding) JSON. You will need to refer to your language's standard or third party libraries to figure out how to decode it. For this example, I will continue using Python as it is simple to read and convert to other languages.

### 4. Decoding Texture Value

With the `value` variable that we found above, you will need to decode from Base64 to UTF-8. This can be done using something like this:

```python
import base64

decoded_value = base64.b64decode(value).decode('utf-8')
```

The value of this `decoded_value` variable will be a JSON object, but still in string format. You will need to load this value into an actual object that we can use:

```python
import json

parsed_value = json.loads(decoded_value)
```

The value of `parsed_value` will now look something like this:

```json
{
	"timestamp": 1647030968205,
	"profileId": "c06f89064c8a49119c29ea1dbd1aab82",
	"profileName": "MHF_Steve",
	"textures": {
		"SKIN": {
			"url": "http://textures.minecraft.net/texture/1a4af718455d4aab528e7a61f86fa25e6a369d1768dcb13f7df319a713eb810b"
		}
	}
}
```

The result above is from a player with a regular (Steve) model skin, which uses 4 pixel wide arms. Minecraft also has another variant of skin which is a slim (Alex) model. This variant uses 3 pixel wide arms. If the model has a slim variant, the response will contain extra metadata properties:

```json
{
	"timestamp": 1647030761810,
	"profileId": "6ab4317889fd490597f60f67d9d76fd9",
	"profileName": "MHF_Alex",
	"textures": {
		"SKIN": {
			"url": "http://textures.minecraft.net/texture/83cee5ca6afcdb171285aa00e8049c297b2dbeba0efb8ff970a5677a1b644032",
			"metadata": {
				"model": "slim"
			}
		}
	}
}
```

You will need to check to see if the `model` value is set to `slim` under the metadata property if you wish to use the player skin for rendering images, or else you will overlap skin components. You can now make a request to the `textures.SKIN.url` value to get the player's skin as a PNG image. This image should either be 64×64 or 64×32 (old skins).

## Old Skins

If you encounter an older skin format (which can be checked if the height of the skin image is 32 pixels), then you will need to do a bit of fiddling to get the components to be extracted properly. In Minecraft versions before 1.8, there was no dedicated skin texture for the left arms and legs. Instead, Minecraft used the corresponding component from the right side and flipped the image horizontally. There was also no overlay (or 2nd layer), which is why the image is only 32 pixels tall instead of the typical 64 pixels in modern formats.

## Alpha Fix

In some skins uploaded to Minecraft, the image is contains opaque or translucent colors where there should be transparency (such as the overlay components). In order to fix the transparency issue, you will need to parse the PNG image into some more easily modifying format that allows you to modify pixel data individually. Here are the steps to fixing the transparency issue:

1. Look at the color and alpha value of the pixel at `(0, 0)` (aka alpha signature)
2. Loop over all pixels in the image and compare them to the value retrieved from step 1
   1. If the R, G, B and alpha values match the alpha signature, then set the alpha value for this current pixel to 255 (or fully opaque).
   2. If any of the R, G, B or alpha values do not match the alpha signature, do not change this pixel and move to the next.
3. Save this modified skin image as a new variable, separate from the original skin image retrieved from Minecraft.

This second alpha-fixed image will only be used for rendering the overlay layer. You will still use the original image for any base layer components.

## Component Coordinates

### Base Skin

| Part      | Direction | Model       | Coordinates           |
| --------- | --------- | ----------- | --------------------- |
| Head      | Top       | Both        | `(8, 0) → (16, 8)`    |
| Head      | Bottom    | Both        | `(16, 0) → (24, 8)`   |
| Head      | Right     | Both        | `(0, 8) → (8, 16)`    |
| Head      | Front     | Both        | `(8, 8) → (16, 16)`   |
| Head      | Left      | Both        | `(16, 8) → (24, 16)`  |
| Head      | Back      | Both        | `(24, 8) → (32, 16)`  |
| Torso     | Top       | Both        | `(20, 16) → (28, 20)` |
| Torso     | Bottom    | Both        | `(28, 16) → (36, 20)` |
| Torso     | Right     | Both        | `(16, 20) → (20, 32)` |
| Torso     | Front     | Both        | `(20, 20) → (28, 32)` |
| Torso     | Left      | Both        | `(28, 20) → (32, 32)` |
| Torso     | Back      | Both        | `(32, 20) → (40, 32)` |
| Left Arm  | Top       | **Steve**   | `(36, 48) → (40, 52)` |
| Left Arm  | Top       | **Alex**    | `(36, 48) → (39, 52)` |
| Left Arm  | Bottom    | **Steve**   | `(40, 48) → (44, 52)` |
| Left Arm  | Bottom    | **Alex**    | `(39, 48) → (42, 52)` |
| Left Arm  | Right     | Both        | `(32, 52) → (36, 64)` |
| Left Arm  | Front     | **Regular** | `(36, 52) → (40, 64)` |
| Left Arm  | Front     | **Slim**    | `(36, 52) → (39, 64)` |
| Left Arm  | Left      | **Regular** | `(40, 52) → (44, 64)` |
| Left Arm  | Left      | **Slim**    | `(39, 52) → (43, 64)` |
| Left Arm  | Back      | **Regular** | `(44, 52) → (48, 64)` |
| Left Arm  | Back      | **Slim**    | `(43, 52) → (46, 64)` |
| Right Arm | Top       | **Steve**   | `(44, 16) → (48, 20)` |
| Right Arm | Top       | **Alex**    | `(44, 16) → (47, 20)` |
| Right Arm | Bottom    | **Steve**   | `(48, 16) → (52, 20)` |
| Right Arm | Bottom    | **Alex**    | `(47, 16) → (50, 20)` |
| Right Arm | Right     | Both        | `(40, 20) → (44, 32)` |
| Right Arm | Front     | **Steve**   | `(44, 20) → (48, 32)` |
| Right Arm | Front     | **Alex**    | `(44, 20) → (47, 32)` |
| Right Arm | Left      | **Steve**   | `(48, 20) → (52, 32)` |
| Right Arm | Left      | **Alex**    | `(47, 20) → (51, 32)` |
| Right Arm | Back      | **Steve**   | `(52, 20) → (56, 32)` |
| Right Arm | Back      | **Alex**    | `(51, 20) → (54, 32)` |
| Left Leg  | Top       | Both        | `(20, 48) → (24, 52)` |
| Left Leg  | Bottom    | Both        | `(24, 48) → (28, 52)` |
| Left Leg  | Right     | Both        | `(16, 52) → (20, 64)` |
| Left Leg  | Front     | Both        | `(20, 52) → (24, 64)` |
| Left Leg  | Left      | Both        | `(24, 52) → (28, 64)` |
| Left Leg  | Back      | Both        | `(28, 52) → (32, 64)` |
| Right Leg | Top       | Both        | `(4, 16) → (8, 20)`   |
| Right Leg | Bottom    | Both        | `(8, 16) → (12, 20)`  |
| Right Leg | Right     | Both        | `(0, 20) → (4, 32)`   |
| Right Leg | Front     | Both        | `(4, 20) → (8, 32)`   |
| Right Leg | Left      | Both        | `(8, 20) → (12, 32)`  |
| Right Leg | Back      | Both        | `(12, 20) → (16, 32)` |

### Overlay

| Part      | Direction | Model     | Coordinates           |
| --------- | --------- | --------- | --------------------- |
| Head      | Top       | Both      | `(40, 0) → (48, 8)`   |
| Head      | Bottom    | Both      | `(48, 0) → (56, 8)`   |
| Head      | Right     | Both      | `(32, 8) → (40, 16)`  |
| Head      | Front     | Both      | `(40, 8) → (48, 16)`  |
| Head      | Left      | Both      | `(48, 8) → (56, 16)`  |
| Head      | Back      | Both      | `(56, 8) → (64, 16)`  |
| Torso     | Top       | Both      | `(20, 48) → (28, 36)` |
| Torso     | Bottom    | Both      | `(28, 48) → (36, 36)` |
| Torso     | Right     | Both      | `(16, 36) → (20, 48)` |
| Torso     | Front     | Both      | `(20, 36) → (28, 48)` |
| Torso     | Left      | Both      | `(28, 36) → (32, 48)` |
| Torso     | Back      | Both      | `(32, 36) → (40, 48)` |
| Left Arm  | Top       | **Steve** | `(52, 48) → (56, 52)` |
| Left Arm  | Top       | **Alex**  | `(52, 48) → (55, 52)` |
| Left Arm  | Bottom    | **Steve** | `(56, 48) → (60, 52)` |
| Left Arm  | Bottom    | **Alex**  | `(55, 48) → (58, 52)` |
| Left Arm  | Right     | Both      | `(48, 52) → (52, 64)` |
| Left Arm  | Front     | **Steve** | `(52, 52) → (56, 64)` |
| Left Arm  | Front     | **Alex**  | `(52, 52) → (55, 64)` |
| Left Arm  | Left      | **Steve** | `(56, 52) → (60, 64)` |
| Left Arm  | Left      | **Alex**  | `(55, 52) → (59, 64)` |
| Left Arm  | Back      | **Steve** | `(60, 52) → (64, 64)` |
| Left Arm  | Back      | **Alex**  | `(59, 52) → (62, 64)` |
| Right Arm | Top       | **Steve** | `(44, 48) → (48, 36)` |
| Right Arm | Top       | **Alex**  | `(44, 48) → (47, 36)` |
| Right Arm | Bottom    | **Steve** | `(48, 48) → (52, 36)` |
| Right Arm | Bottom    | **Alex**  | `(47, 48) → (50, 36)` |
| Right Arm | Right     | Both      | `(40, 36) → (44, 48)` |
| Right Arm | Front     | **Steve** | `(44, 36) → (48, 48)` |
| Right Arm | Front     | **Alex**  | `(44, 36) → (47, 48)` |
| Right Arm | Left      | **Steve** | `(48, 36) → (52, 48)` |
| Right Arm | Left      | **Alex**  | `(47, 36) → (51, 48)` |
| Right Arm | Back      | **Steve** | `(52, 36) → (56, 48)` |
| Right Arm | Back      | **Alex**  | `(51, 36) → (54, 48)` |
| Left Leg  | Top       | Both      | `(4, 48) → (8, 52)`   |
| Left Leg  | Bottom    | Both      | `(8, 48) → (12, 52)`  |
| Left Leg  | Right     | Both      | `(0, 52) → (4, 64)`   |
| Left Leg  | Front     | Both      | `(4, 52) → (8, 64)`   |
| Left Leg  | Left      | Both      | `(8, 52) → (12, 64)`  |
| Left Leg  | Back      | Both      | `(12, 52) → (16, 64)` |
| Right Leg | Top       | Both      | `(4, 48) → (8, 36)`   |
| Right Leg | Bottom    | Both      | `(8, 48) → (12, 36)`  |
| Right Leg | Right     | Both      | `(0, 36) → (4, 48)`   |
| Right Leg | Front     | Both      | `(4, 36) → (8, 48)`   |
| Right Leg | Left      | Both      | `(8, 36) → (12, 48)`  |
| Right Leg | Back      | Both      | `(12, 36) → (16, 48)` |
