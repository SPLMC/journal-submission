---
permalink: /contacts
layout: default
---

{% for member in site.data.contacts %}
  * [{{ member.name }}]({{ member.cv }})
{% endfor %}
