---
description: Retrieve the raw skin image of any Minecraft player.
---

# 🏔 Raw Skin

{% swagger method="get" path="/skin/:user" baseUrl="https://api.mineatar.io" summary="Raw Skin" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="user" required="true" %}
A username or UUID
{% endswagger-parameter %}

{% swagger-parameter in="query" name="download" type="Boolean" %}
Force the browser to open a save file dialog
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}


![](<../.gitbook/assets/image (3).png>)


{% endswagger-response %}
{% endswagger %}
