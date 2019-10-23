---
layout: page
title: Step-by Step Tutorials
---

<h3>Getting Started</h3>
<ul class="posts">
  {% assign posts_in_order = site.posts | sort %}
  {% for post in posts_in_order %}
    {% if post.post_type == "getting_started" %}
    <li itemscope>
      <a href="{{ site.github.url }}{{ post.url }}">{{ post.title }}</a>
      <p class="post-date"><span><i class="fa fa-clock-o" aria-hidden="true"></i> {% include read-time.html %}</span></p>
    </li>
    {% endif %}
  {% endfor %}

<h3>Supplemental</h3>
<ul class="posts">
  {% for post in site.posts %}
    {% if post.post_type == "supplementary" %}
    <li itemscope>
      <a href="{{ site.github.url }}{{ post.url }}">{{ post.title }}</a>
      <p class="post-date"><span><i class="fa fa-clock-o" aria-hidden="true"></i> {% include read-time.html %}</span></p>
    </li>
    {% endif %}

  {% endfor %}
</ul>

<h3>Using OrthoFinder for Comparative Genomics</h3>
<ul class="posts">
  {% for post in site.posts %}
    {% if post.post_type == "applications" %}
    <li itemscope>
      <a href="{{ site.github.url }}{{ post.url }}">{{ post.title }}</a>
      <p class="post-date"><span><i class="fa fa-clock-o" aria-hidden="true"></i> {% include read-time.html %}</span></p>
    </li>
    {% endif %}

  {% endfor %}
</ul>
