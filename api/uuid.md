---
description: Utility routes for getting the UUID of a player by username.
---

# UUID

{% swagger method="get" path="/uuid/:user" baseUrl="https://api.mineatar.io" summary="Get Player UUID" %}
{% swagger-description %}

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
