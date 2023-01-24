---
layout: default
title: 글 목록 분류
permalink: /category/
---

{% capture site_categories %}{% for category in site.categories %}{{ category | first }}{% unless forloop.last %},{% endunless %}{% endfor %}{% endcapture %}
{% assign categories_list = site_categories | split:',' | sort %}

  <h1>Category</h1>

  --------------------------------------------
  {% for item in (0..site.categories.size) %}{% unless forloop.last %}
  {% capture this_word %}{{ categories_list[item] | strip_newlines }}{% endcapture %}
  <div style="margin-bottom: 30px;">
  <div id="{{this_word}}"></div>
  <h2>{{this_word}}</h2>
  
  <ul>
    {% for post in site.categories[this_word] %}{% if post.title != null %}
    <li>

    <h3>
      <p> ({{ post.date | date: "%Y-%b-%-d" }}) <a href="{{ site.url }}{{ site.baseurl }}{{ post.url }}">{{ post.title | escape }}</a></p>
     </h3>
    </li>
    {% endif %}{% endfor %}
  </ul>
</div>
{% endunless %}{% endfor %}