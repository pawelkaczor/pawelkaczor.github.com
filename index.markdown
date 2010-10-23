---
layout: default
title: "Pawel Kaczor - blog"
description: "Blog Pawła Kaczora, o programowaniu aplikacji biznesowych."
---
<div class="related">
<h2 style="padding-top:1em;" class="green">Wpisy:</h2>
  <ul>{% for post in site.posts %}<li><a href="{{ post.url }}">{{ post.title }}</a></li>{% endfor %}</ul>
</div>
{% for page in site.posts limit:5 %}
{% assign body = page.content %}
{% include post-div.html %}
{% if page.comments %}

<div id="disqus_thread"></div>

<script
   type="text/javascript"
   src="http://disqus.com/forums/Newion/embed.js">
</script>
<noscript>
  <a href="http://Newion.disqus.com/?url=ref">View the discussion thread.</a>
</noscript>

<a href="http://disqus.com" class="dsq-brlink">
  blog comments powered by <span class="logo-disqus">Disqus</span>
</a>

{% endif %}
{% endfor %}

<div class="related">
  <div id="rest">
	<div>
		<div>
		    <h2><a href="http://pkaczor.blogspot.com" id="blog-link" style="text-align:left;">read my blog!</a> <img alt="blog" src="http://img1.blogblog.com/img/navbar/icons_orange.png"/></h2>
		</div>
	</div>
    <div class="twitter">
      <div id="twitter_div">
        <h2 class="sidebar-title">ćwierkanie! <img alt="twitter" src="/images/twitter_48.png"/></h2>
        <ul id="twitter_update_list"><li></li></ul>
        <a href="http://twitter.com/Newion" id="twitter-link" style="display:block;text-align:right;">follow me on Twitter</a>
      </div>
    </div>
    <script type="text/javascript" src="http://twitter.com/javascripts/blogger.js"></script>
    <script type="text/javascript" src="http://twitter.com/statuses/user_timeline/Newion.json?callback=twitterCallback2&amp;count=2"></script>

  </div>
</div>
