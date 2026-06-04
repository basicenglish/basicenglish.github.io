---
layout: page_
title: "Basic English"
video_id: xNnrVmNyRxw
permalink: /
---
<h1>Basic English Ordered Wordlist</h1>

{% assign wiki_order = "operations,things,picturable,qualities,opposites" | split: "," %}

{% for group_slug in wiki_order %}
  {% assign current_words = site.words | where: "group", group_slug %}
  
  {% if current_words.size > 0 %}
    <div class="word-group-section">
      <h2>{{ group_slug | replace: "_", " " | capitalize }}</h2>
      
      <ul class="word-list">
        {% assign sorted_words = current_words | sort: "position" %}
        {% for word in sorted_words %}
          <li>
            <a href="{{ word.url }}"><strong>{{ word.title }}</strong></a>
          </li>
        {% endfor %}
      </ul>
    </div>
  {% endif %}
{% endfor %}
