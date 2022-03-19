---
description: Render the player's head as an isometric projection.
---

# 🧑🦱 Head

{% swagger method="get" path="/head/:user" baseUrl="https://api.mineatar.io" summary="Render Head" %}
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


![](<../.gitbook/assets/image (4).png>)


{% endswagger-response %}
{% endswagger %}
