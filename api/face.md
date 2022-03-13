---
description: Render the face of a Minecraft player as a 2D image.
---

# 😁 Face

{% swagger method="get" path="/face/:user" baseUrl="https://api.mineatar.io" summary="Face" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="user" required="true" %}
A username or UUID
{% endswagger-parameter %}

{% swagger-parameter in="query" name="scale" type="Number" %}
A scaling value of the image
{% endswagger-parameter %}

{% swagger-parameter in="query" name="overlay" type="Boolean" %}
Enable or disable skin overlay
{% endswagger-parameter %}

{% swagger-parameter in="query" name="download" type="Boolean" %}
Force the browser to download the image
{% endswagger-parameter %}
{% endswagger %}

![MHF\_Steve's Face](https://api.mineatar.io/face/MHF\_Steve?scale=16)
