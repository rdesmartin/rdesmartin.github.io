---
layout: page
title: My notes
permalink: /notes
---

I keep my notes here as a [digital garden](https://maggieappleton.com/garden-history), meaning there will be very rough drafts and things unrelated to computer science or verification kept here.


<div class="papers">
    <ul>
        {% for note in site.notes %}
        <li><a href="{{ note.url }}">{{ note.title }}</a></li>
        {% endfor %}
    </ul>
</div>
