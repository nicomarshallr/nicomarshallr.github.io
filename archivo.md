---
layout: default
title: Archivo de Publicaciones
permalink: /archivo/
---

<div class="archive-header">
    <h1 class="page-title">{{ page.title }}</h1>
</div>



{% assign postsPorMesAno = site.posts | group_by_exp: "post", "post.date | date: '%B %Y'" %}
{% for mesAno in postsPorMesAno %}
  <h2>{{ mesAno.name }}</h2>
  <ul>
    {% for post in mesAno.items %}
      <li><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
  </ul>
{% endfor %}
