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
A scaling value of the image (default: 

`4`

)
{% endswagger-parameter %}

{% swagger-parameter in="query" name="overlay" type="Boolean" %}
Enable or disable skin overlay (default: 

`true`

)
{% endswagger-parameter %}

{% swagger-parameter in="query" name="download" type="Boolean" %}
Force the browser to download the image (default: 

`false`

)
{% endswagger-parameter %}

{% swagger-parameter in="query" name="fallback" type="Boolean" %}
Fallback to default skin if unavailable (default: 

`true`

)
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}


![](<../.gitbook/assets/image (5).png>)


{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/body/front/:user" baseUrl="https://api.mineatar.io" summary="Render Front of Body" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="user" required="true" %}
A username or UUID
{% endswagger-parameter %}

{% swagger-parameter in="query" name="scale" type="Number" %}
A scaling value of the image (default: 

`4`

)
{% endswagger-parameter %}

{% swagger-parameter in="query" name="overlay" type="Boolean" %}
Enable or disable skin overlay (default: 

`true`

)
{% endswagger-parameter %}

{% swagger-parameter in="query" name="download" type="Boolean" %}
Force the browser to download the image (default: 

`false`

)
{% endswagger-parameter %}

{% swagger-parameter in="query" name="fallback" type="Boolean" %}
Fallback to default skin if unavailable (default: 

`true`

)
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}


![](<../.gitbook/assets/image (6).png>)


{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/body/back/:user" baseUrl="https://api.mineatar.io" summary="Render Back of Body" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="user" required="true" %}
A username or UUID
{% endswagger-parameter %}

{% swagger-parameter in="query" name="scale" type="Number" %}
A scaling value of the image (default: 

`4`

)
{% endswagger-parameter %}

{% swagger-parameter in="query" name="overlay" type="Boolean" %}
Enable or disable skin overlay (default: 

`true`

)
{% endswagger-parameter %}

{% swagger-parameter in="query" name="download" type="Boolean" %}
Force the browser to download the image (default: 

`false`

)
{% endswagger-parameter %}

{% swagger-parameter in="query" name="fallback" type="Boolean" %}
Fallback to default skin if unavailable (default: 

`true`

)
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}


![](<../.gitbook/assets/image (2).png>)


{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/body/left/:user" baseUrl="https://api.mineatar.io" summary="Render Left Side of Body" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="user" %}
A username or UUID
{% endswagger-parameter %}

{% swagger-parameter in="query" name="scale" type="Number" %}
A scaling value of the image (default: 

`4`

)
{% endswagger-parameter %}

{% swagger-parameter in="query" name="overlay" type="Boolean" %}
Enable or disable skin overlay (default: 

`true`

)
{% endswagger-parameter %}

{% swagger-parameter in="query" name="download" type="Boolean" %}
Force the browser to download the image (default: 

`false`

)
{% endswagger-parameter %}

{% swagger-parameter in="query" name="fallback" type="Boolean" %}
Fallback to default skin if unavailable (default: 

`true`

)
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}


![](<../.gitbook/assets/image (7).png>)


{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/body/right/:user" baseUrl="https://api.mineatar.io" summary="Render Right Side of Body" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="user" %}
A username or UUID
{% endswagger-parameter %}

{% swagger-parameter in="query" name="scale" type="Number" %}
A scaling value of the image  (default: 

`4`

)
{% endswagger-parameter %}

{% swagger-parameter in="query" name="overlay" type="Boolean" %}
Enable or disable skin overlay (default: 

`true`

)
{% endswagger-parameter %}

{% swagger-parameter in="query" name="download" type="Boolean" %}
Force the browser to download the image (default: 

`false`

)
{% endswagger-parameter %}

{% swagger-parameter in="query" name="fallback" type="Boolean" %}
Fallback to default skin if unavailable (default: 

`true`

)
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}


![](<../.gitbook/assets/image (1).png>)


{% endswagger-response %}
{% endswagger %}
