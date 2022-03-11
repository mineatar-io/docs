---
description: Utility routes for getting the UUID of a player by username.
---

# 🔭 UUID

{% swagger method="get" path="/uuid/:user" baseUrl="https://api.mineatar.io" summary="Get Player UUID" %}
{% swagger-description %}
Please note that you should never check the body content to confirm whether the request was successful. Use the status code returned from the response instead. 

`200`

 means the player was successfully found, and 

`404`

 means the player was not found from Mojang's API.
{% endswagger-description %}

{% swagger-parameter in="path" name="user" required="true" %}
A username or UUID
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="The user was found" %}
```javascript
c06f89064c8a49119c29ea1dbd1aab82
```
{% endswagger-response %}

{% swagger-response status="404: Not Found" description="The user was not found" %}
```javascript
Not Found
```
{% endswagger-response %}
{% endswagger %}
