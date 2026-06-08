---
layout: page
title: Papers
permalink: /papers
---

I keep notes on interesting papers I read here.

<div class="papers"> 
    <ul>
        {% for paper in site.papers %}
            <li><a href="{{ paper.url }}">{{ paper.title }}</a></li>
        {% endfor %}
    </ul>
</div>
