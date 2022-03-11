---
description: >-
  Render the player's body as either a 2D flat image or a 3D isometric
  projection.
---

# Body

{% swagger method="get" path="/body/full/:user" baseUrl="https://api.mineatar.io" summary="Render Full Body" %}
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

![](<../.gitbook/assets/image (4).png>)

{% swagger method="get" path="/body/front/:user" baseUrl="https://api.mineatar.io" summary="Render Front of Body" %}
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
