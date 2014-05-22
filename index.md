---
layout: page
title: DMing
tagline: Do something to sparkle your life.
---

{% include JB/setup %}

#### Maybe you are a big fan of various aspects of data mining. Welcome!

![HeBei]({{ site.url}}/assets/images/hebei.jpg)

<div class="nav">
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">
          <h1> {{ post.title }} </h1> 
       </a>
      <span>{{ post.date | date: "%d %B %Y" }}</span>
      <article>{{ post.excerpt }}</article>
    </li>
  {% endfor %}
</div>