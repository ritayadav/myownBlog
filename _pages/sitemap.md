---
layout: archive
title: "Sitemap"
permalink: /sitemap/
author_profile: false
---

{% include base_path %}

<h2>Posts</h2>
{% for post in site.posts %}
  {% include archive-single.html %}
{% endfor %}
