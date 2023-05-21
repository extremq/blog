---
layout: default
title: Home
---

# Who I am

I go by my online alias "Extremq", and I am a computer science enthusiast who thrives by helping others and creating all kinds of things.

You can also find my other presences online on [GitHub]({{ site.github }}) and [YouTube]({{ site.youtube }}), or contact me on [{{ site.email }}](mailto: {{ site.email }}). 

For more info, check out the [About](/about) page.

# Articles

I love writing about ideas I've encountered or projects I developed. Take a look.

{% assign postsByYearMonth = site.posts | group_by_exp: "post", "post.date | date: '%B %Y'" %}
{% for yearMonth in postsByYearMonth %}
  <h2>{{ yearMonth.name }}</h2>
  <ul>
    {% for post in yearMonth.items %}
      <li><a href="{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
  </ul>
{% endfor %}
