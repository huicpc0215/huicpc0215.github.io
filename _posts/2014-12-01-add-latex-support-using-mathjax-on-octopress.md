---
layout: post
title: "Add Latex Support Using Mathjax on Octopress"
modified:
categories: 
description: add latex support 
tags: [latex, Mathjax, Octopress]
image:
  feature: abstract-5.jpg
  credit: dargadgetz
  creditlink:
share: true
date: 2014-12-01T21:14:24+08:00
---


Just follow this [instructions](http://www.idryman.org/blog/2012/03/10/writing-math-equations-on-octopress/ )

<!--more-->

---

1.edit `_config.yml`
{% highlight html %}
>markdown=kramdown
{% endhighlight %}
2.edit `Gemfile`
{% highlight html %}
gem ‘kramdown’
{% endhighlight %}
3.add mathjax to `_include/head.html`
{% highlight html %}
<!-- mathjax config similar to math.stackexchange -->
<script type="text/x-mathjax-config">
MathJax.Hub.Config({
  jax: ["input/TeX", "output/HTML-CSS"],
  tex2jax: {
    inlineMath: [ ['$', '$'] ],
    displayMath: [ ['$$', '$$']],
    processEscapes: true,
    skipTags: ['script', 'noscript', 'style', 'textarea', 'pre', 'code']
  },
  messageStyle: "none",
  "HTML-CSS": { preferredFont: "TeX", availableFonts: ["STIX","TeX"] }
});
</script>
<script src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS_HTML" type="text/javascript"></script>
{% endhighlight %}

all done!

Let’s have a test:

$$
E=MC^2
$$
