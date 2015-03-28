---
layout: default
title: Hi there
---

<header>
  <h1>{{ page.title }}</h1>
</header>

<article>
  {{ site.description }}
</article>

{% for post in paginator.posts %}
<article>
  <h2>
    <a href="{{ post.url | prepend: site.baseurl }}" title="{{ post.title }}">
      {{ post.title }}
    </a>
  </h2>
  <p>{{ post.excerpt }}</p>
  {% if post.file %}
  <audio src="{{ post.file }}" preload="auto" controls="controls" type="audio/mp3">
    Your browser doesn't support the <code>audio</code> element.
  </audio>

  <a href="{{ post.file }}" class="button">Download</a>
  {% endif %}

  {% if post.soundcloud %}
  {{ post.soundcloud }}
  {% endif %}
</article>
{% endfor %}

<nav class="pagination">
  {% if paginator.previous_page %}
    {% if paginator.previous_page == 1 %}
    <a href="/" class="previous">← Newer</a>
    {% else %}
    <a href="/posts/{{ paginator.previous_page }}" class="previous">← Newer</a>
    {% endif %}
  {% endif %}
  {% if paginator.next_page %}
    <a href="/posts/{{ paginator.next_page }}" class="next">Older →</a>
  {% endif %}
</nav>