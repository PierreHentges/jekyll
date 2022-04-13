---
title: Projects
layout: default
permalink: /projects/
collection: projects
---
{% for projects in site.projects %}
  <h2> 
    <a href="{{ projects.url }}">
      {{projects.title}}
    </a>
  </h2>
  <p>{{ projects.excerpt | markdownify }}</p>
{% endfor %}
