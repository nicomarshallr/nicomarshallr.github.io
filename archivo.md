---
layout: default
title: Archivo de Publicaciones
permalink: /archivo/
---

<div class="archive-header">
    <h1 class="page-title">{{ page.title }}</h1>
</div>

{% assign current_year = '' %}

{% for post in site.posts %}
    {% assign post_year = post.date | date: "%Y" %}
    
    {% if post_year != current_year %}
        {% unless forloop.first %}</ul>{% endunless %}
        <h2 style="margin-top: 30px; border-bottom: 1px solid #eee; padding-bottom: 5px;">{{ post_year }}</h2>
        <ul style="list-style: none; padding-left: 0;">
        {% assign current_year = post_year %}
    {% endif %}

    <li style="margin-bottom: 5px;">
        <time datetime="{{ post.date | date_to_xmlschema }}" style="color: #999; font-size: 14px; margin-right: 10px;">
            {{ post.date | date: "%b %d" }}
        </time>
        <a href="{{ site.baseurl }}{{ post.url }}" style="text-decoration: none;">{{ post.title }}</a>
    </li>
    
    {% if forloop.last %}</ul>{% endif %}
{% endfor %}