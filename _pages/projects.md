---
layout: page
title: projects
permalink: /projects/
description: "Projects by Will Rowan: PXLD (AI filmmaking tools), opencall.fyi, Swingometer, and more. Startups, platforms, creative works, and civic tech."
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
