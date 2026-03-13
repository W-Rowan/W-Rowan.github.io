---
layout: page
title: projects
permalink: /projects/
description: Things I have built, from startups and platforms to creative works and civic tech.
nav: true
nav_order: 3
horizontal: false
---

<div class="projects">
{% assign sorted_projects = site.projects | sort: "importance" %}
<div class="grid">
  {% for project in sorted_projects %}
    {% include projects.html %}
  {% endfor %}
</div>
</div>
