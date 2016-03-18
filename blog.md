---
layout: page
title: Blog
heading: Just a simple blog
---

These are the remainings of my personal blog. The content below was originally
published on nach-vorne.de and blog.schm.eu. Unfortunately I did not manage to
continue my writing, but I keep the content alive, since I think it is still
valid. The topics were fueled by my daily work, so expect them to be technical,
mostly ruby and web related.

## Latest posts

<ul class="posts">
{% for post in site.posts limit: 5 %}
  <li>
    <span>{{ post.date | date: "%B %e, %Y" }}</span>
    &raquo;
    <a href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
  </li>
{% endfor %}
</ul>

<div class="smallprint" markdown="1">

## Archive

{% for post in site.posts  %}

  {% capture this_year %}{{ post.date | date: "%Y" }}{% endcapture %}
  {% capture this_month %}{{ post.date | date: "%B" }}{% endcapture %}
  {% capture next_year %}{{ post.previous.date | date: "%Y" }}{% endcapture %}
  {% capture next_month %}{{ post.previous.date | date: "%B" }}{% endcapture %}

  {% if forloop.first %}

<h2>{{this_year}}</h2>
<h3>{{this_month}}</h3>
<ul>

  {% endif %}

  <li>
  <span>{{ post.date | date: "%B %e, %Y" }}</span>
  &raquo;
  <a href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
  </li>

  {% if forloop.last %}

</ul>

  {% else %}
    {% if this_year != next_year %}

</ul>

<h2>{{next_year}}</h2>
<h3>{{next_month}}</h3>

<ul>

  {% else %}
    {% if this_month != next_month %}

</ul>

<h3>{{next_month}}</h3>

<ul>

    {% endif %}
  {% endif %}
{% endif %}

{% endfor %}

</div>