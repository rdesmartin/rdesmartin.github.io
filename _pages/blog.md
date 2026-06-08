---
layout: page
title: My blog
permalink: /blog
---

<div class="notes">
    <ul>
        {% for post in site.posts %}
        <li><a href="{{ post.url }}">{{ post.title }}</a></li>
        {% endfor %}
    </ul>
</div>
