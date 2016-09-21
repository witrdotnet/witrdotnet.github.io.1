---
layout: page
title: witrdotnet
tagline: IT blog
---
{% include JB/setup %}

<div>
  {% for post in site.posts limit:5 %}
    <a href="{{ post.url }}"><h3 class="post_title">{{ post.title }}</h3></a>
    <p class="post_date">{{ post.date | date: "%d %B %Y" }}</p>
    <div class="post_box">
      <div>{{ post.content }}</div>
    </div>
    <hr/>
  {% endfor %}
</div>

## Posts

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>
