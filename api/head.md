---
description: Render the player's head as an isometric projection.
---

# Head

{% swagger method="get" path="/head/:user" baseUrl="https://api.mineatar.io" summary="Render Head" %}
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

![](<../.gitbook/assets/image (3) (1).png>)
