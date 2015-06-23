---
layout: post
title:  "And It Begins!"
date:   2015-06-29 22:40:00
categories: Gsoc'15 updates
tags: featured
image: /assets/article_images/2014-08-29-welcome-to-jekyll/desktop.jpg
---
And so it begins..

This is a blog i am gonna maintain during the summer. I am going to use it to keep the readers updated about Drupal's url-embed module, which i am developing as part of Google Summer Of Code'15.(GSOC'15)

Those of you who are not aware of what GSOC is let me just brief you, it is basically to promote open source development and spread awareness about open source by funding projects that contribute to open source organisations such as Drupal.

**So what am i going to do in this project?**

The idea is very simple, if i want to share a video on facebook all i need to do is paste the url as my facebook status and it gets converted to a thumbnail, where a my friends can click and watch it, so a Drupal user should be able to do the same, essentially paste a url in a WYSIWYG Editorsuch as CKEditor which comes with Drupal-8, and it gets converted to a mini version of its content, the content could be a video, raw-text , image etc..

**So how are we gonna do it?**

Well, that is what this blog is for, for the starters we'll let the heavy work be done by OscarOtereo's Embed library. and that is what i explored this week. you can also look into it and read more about it by clicking here...

In the nextt week I will work on something very obvious.. in order to embed a url's content we need to identify a url and replace it, with its content that is what *Text Filters* do,and that is what I am gonna write this week...

{% highlight js %}

<footer class="site-footer">
 <a class="subscribe" href="{{ "/feed.xml" | prepend: site.baseurl }}"> <span class="tooltip"> <i class="fa fa-rss"></i> Subscribe!</span></a>
  <div class="inner">a
   <section class="copyright">All content copyright <a href="mailto:{{ site.email}}">{{ site.name }}</a> &copy; {{ site.time | date: '%Y' }} &bull; All rights reserved.</section>
   <section class="poweredby">Made with <a href="http://jekyllrb.com"> Jekyll</a></section>
  </div>
</footer>
{% endhighlight %}


[jekyll]:      http://jekyllrb.com
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-help]: https://github.com/jekyll/jekyll-help
