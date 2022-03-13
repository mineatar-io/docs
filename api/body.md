---
description: >-
  Render the player's body as either a 2D flat image or a 3D isometric
  projection.
---

# 🧍 Body

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

![MHF\_Steve's Full Body](https://api.mineatar.io/body/full/MHF\_Steve?scale=8)

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

![MHF\_Steve's Front Body](https://api.mineatar.io/body/front/MHF\_Steve?scale=8)

{% swagger method="get" path="/body/back/:user" baseUrl="https://api.mineatar.io" summary="Render Back of Body" %}
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

![MHF\_Steve's Back Body](https://api.mineatar.io/body/back/MHF\_Steve?scale=8)

{% swagger method="get" path="/body/left/:user" baseUrl="https://api.mineatar.io" summary="Render Left Side of Body" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="user" %}
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

![MHF\_Steve's Left Body](https://api.mineatar.io/body/left/MHF\_Steve?scale=8)

{% swagger method="get" path="/body/right/:user" baseUrl="https://api.mineatar.io" summary="Render Right Side of Body" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="user" %}
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

![MHF\_Steve's Right Body](https://api.mineatar.io/body/right/MHF\_Steve?scale=8)
