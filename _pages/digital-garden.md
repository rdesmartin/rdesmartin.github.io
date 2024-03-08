---
layout: page
title: Digital garden
id: home
permalink: /digital-garden
---

<strong>Recently updated notes</strong>

<ul>
  {% assign recent_notes = site.notes | sort: "last_modified_at_timestamp" | reverse %}
  {% for note in recent_notes limit: 5 %}
    <li>
      {{ note.last_modified_at | date: "%Y-%m-%d" }} — <a class="internal-link" href="{{ note.url }}">{{ note.title }}</a>
    </li>
  {% endfor %}
</ul>

<strong>Recently added papers</strong>
<ul>
  {% assign recent_papers = site.papers | sort: "last_modified_at_timestamp" | reverse %}
  {% for paper in recent_papers limit: 5 %}
    <li>
      {{ paper.last_modified_at | date: "%Y-%m-%d" }} — <a class="internal-link" href="{{ paper.url }}">{{ paper.title }}</a>
    </li>
  {% endfor %}
</ul>

<style>
  .wrapper {
    max-width: 46em;
  }
</style>
