---
layout: page
title: Hello World!
tagline: Supporting tagline
---
{% include JB/setup %}

<div>
    {% for post in site.posts limit 4 %}
	<p>
		<span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a>
	</p>
	<div>
		 {{ post.content | strip_html | truncatewords:75}}<br>
         <a href="{{ post.url }}">Read more...</a><br><br>
	</div>   
    {% endfor %}
</div>
