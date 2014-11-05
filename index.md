---
layout: page
title: "Rankcloud"
description: ""
paginate: 3
---
{% include JB/setup %}



<div class='row' style='margin-top: 20px;'>

<div class='col-sm-10 col-sm-offset-1'>
  {% for post in site.posts %}
  <div class='panel panel-default'>
    <div class='panel-heading'>
      <h2 class='posts-title'><a href='{{ BASE_PATH }}{{ post.url }}'>{{ post.title }}</a></h2>
      <p class='posts-date'>{{ post.date | date: '%Y-%m-%d' }}</p>
    </div>
    <div class='panel-body'>
      {{ post.content }}
    </div>
  </div>
  {% endfor %}
</div>

<div class='col-xs-12 text-center'>
  {% if site.total_pages > 1 %}
  <ul class='pagination'>
    {% if site.previous_page %}
      <li><a href='{{ BASE_PATH }}{{ site.first_page_path }}'>&laquo; 처음</a></li>
      <li><a href='{{ BASE_PATH }}{{ site.previous_page_path }}'>&lt; 이전</a></li>
    {% else %}
      <li class='disabled'><span>&laquo; 처음</span></li>
      <li class='disabled'><span>&lt; 이전</span></li>
    {% endif %}

    {% if site.page > 3 %}
      <li class='disabled'><span>&hellip;</span></li>
    {% endif %}

    {% for cur in (1..site.total_pages) %}
      {% assign two_less = cur | minus: 2 %}
      {% assign two_more = cur | plus: 2 %}
      {% if site.page < two_less or site.page > two_more %}
      {% elsif cur == site.page %}
        <li class='active'><span>{{ cur }}</span></li>
      {% elsif cur == 1 %}
        <li><a href='{{ BASE_PATH }}/ko/'>{{ cur }}</a></li>
      {% else %}
        <li><a href='{{ BASE_PATH }}{{ page.paginate_path | replace: ':num', cur }}'>{{ cur }}</a></li>
      {% endif %}
    {% endfor %}

    {% assign total_minus_2 = site.total_pages | minus: 2 %}
    {% if site.page < total_minus_2 %}
      <li class='disabled'><span>&hellip;</span></li>
    {% endif %}

    {% if site.next_page %}
      <li><a href='{{ BASE_PATH }}{{ site.next_page_path }}'>다음 &gt;</a></li>
      <li><a href='{{ BASE_PATH }}{{ site.last_page_path }}'>끝 &raquo;</a></li>
    {% else %}
      <li class='disabled'><span>다음 &gt;</span></li>
      <li class='disabled'><span>끝 &raquo;</span></li>
    {% endif %}
  </ul>
  {% endif %}
</div>

</div>