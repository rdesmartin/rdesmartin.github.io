---
layout: page
title: My notes
permalink: /notes
---

I keep my notes here as a [digital garden](https://maggieappleton.com/garden-history), meaning there will be very rough drafts and things unrelated to computer science or verification kept here.

<h2>Computer Science</h2>
<div class="papers">
    <ul>
        {% for note in site.notes %}
        {% if note.tags contains "research" %}
            <li><a href="{{ note.url }}">{{ note.title }}</a></li>
        {% endif %}
        {% endfor %}
    </ul>
</div>


<h2>Programming Notes</h2>
<div class="papers">
    <ul>
        {% for note in site.notes %}
        {% if note.tags contains "programming" %}
            <li><a href="{{ note.url }}">{{ note.title }}</a></li>
        {% endif %}
        {% endfor %}
    </ul>
</div>


<h2>Random Musings</h2>
<div class="papers">
    <ul>
        {% for note in site.notes %}
        {% if note.tags contains "misc" %}
            <li><a href="{{ note.url }}">{{ note.title }}</a></li>
        {% endif %}
        {% endfor %}
    </ul>
</div>
