---
# You don't need to edit this file, it's empty on purpose.
# Edit theme's home layout instead if you wanna make some changes
# See: https://jekyllrb.com/docs/themes/#overriding-theme-defaults
layout: home
---

<div class="intro-col-wrapper">
    <div class="intro-col intro-col-1">
        <img src="{{ "/assets/my_photo.png" }}" alt="my_photo" height="150px">
    </div>
    <div class="intro-col intro-col-2">
        <h2 id="hi-there">Hi there!</h2>
        <p>I’m a software engineer who has a passion for system programing, low-level technologies, and embedded hardware design.</p>
        <p>If you’d like to chat, feel free to <a href="mailto:{{ site.email }}">send me an email</a></p>
    </div>
</div>

## Projects

<div class="projects-cards">
  <!-- WolfieMouse -->
  <div class="github-card" data-gh-project="kbumsik/WolfieMouse">
    <header class="github-card-header">
      <p class="github-card-suptitle">On <a href="https://github.com/kbumsik/WolfieMouse" title="View on   GitHub">GitHub</a></p>
      <h1 class="github-card-title"><a href="https://github.com/kbumsik/WolfieMouse" title="View   more">WolfieMouse</a></h1>
    </header>
    <div class="github-card-body">
      <dl class="github-card-details">
        <dt>Forked</dt>
        <dd class="github-fork"><a href="https://github.com/kbumsik/WolfieMouse/fork" title="View fork   details"><!-- Fork count via javascript --></a></dd>
        <dt>Starred</dt>
        <dd class="github-star"><a href="https://github.com/kbumsik/WolfieMouse/stargazers" title="View fork   details"><!-- Stargazers count via javascript --></a></dd>
      </dl>
    </div>
  </div>
  <!-- VirtScreen -->
  <div class="github-card" data-gh-project="kbumsik/VirtScreen">
    <header class="github-card-header">
      <p class="github-card-suptitle">On <a href="https://github.com/kbumsik/VirtScreen" title="View on  GitHub">GitHub</a></p>
      <h1 class="github-card-title"><a href="https://github.com/kbumsik/VirtScreen" title="View  more">VirtScreen</a></h1>
    </header>
    <div class="github-card-body">
      <dl class="github-card-details">
        <dt>Forked</dt>
        <dd class="github-fork"><a href="https://github.com/kbumsik/VirtScreen/fork" title="View fork details"><!--  Fork count via javascript --></a></dd>
        <dt>Starred</dt>
        <dd class="github-star"><a href="https://github.com/kbumsik/VirtScreen/stargazers" title="View fork  details"><!-- Stargazers count via javascript --></a></dd>
      </dl>
    </div>
  </div>
  <!-- opus-media-recorder -->
  <div class="github-card" data-gh-project="kbumsik/opus-media-recorder">
    <header class="github-card-header">
      <p class="github-card-suptitle">On <a href="https://github.com/kbumsik/opus-media-recorder" title="View on  GitHub">GitHub</a></p>
      <h1 class="github-card-title"><a href="https://github.com/kbumsik/opus-media-recorder" title="View  more">opus-media-recorder</a></h1>
    </header>
    <div class="github-card-body">
      <dl class="github-card-details">
        <dt>Forked</dt>
        <dd class="github-fork"><a href="https://github.com/kbumsik/opus-media-recorder/fork" title="View fork details"><!--  Fork count via javascript --></a></dd>
        <dt>Starred</dt>
        <dd class="github-star"><a href="https://github.com/kbumsik/opus-media-recorder/stargazers" title="View fork  details"><!-- Stargazers count via javascript --></a></dd>
      </dl>
    </div>
  </div>
</div>

<br/>

## Posts

<ul class="post-list">
  {% for post in site.posts %}
    <li>
      {% assign date_format = site.minima.date_format | default: "%b %-d, %Y" %}
      <span class="post-meta">{{ post.date | date: date_format }}</span>
      <h2>
        <a class="post-link" href="{{ post.url | relative_url }}">{{ post.title | escape }}</a>
      </h2>
    </li>
  {% endfor %}
</ul>
<p class="rss-subscribe">subscribe <a href="{{ "/feed.xml" | relative_url }}">via RSS</a></p>
