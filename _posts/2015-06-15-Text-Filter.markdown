---
layout: post
title:  "Url Embed Text Filter Plugin"
date:   2015-06-15 22:40:00
categories: Gsoc'15 updates
tags: featured
image: /assets/article_images/2014-08-29-welcome-to-jekyll/desktop.jpg
---
So this week we had our first hangout meeting , which was very essential, and gave me a very good prespective on how to move forward.

As per the progress is concerned, i finished writing a *Text Filter* for our module, Text filters are developed as a Plugins in Drupal 8. So basically the idea is that if a user wants to embed a url, he should provide us certain attributes for the url, one offcourse would be the url itself, other that that he should be able to tell us the source and/ or the Oembed provider for that. 

**Now what exactly is Omembed Provider?**
To keep it very simple Oembed providers are service providers which returns the data(media) in a json/XML or certain other formats if they are passed a url for the source for which they serve, for example, youtube will have a service provider for them which will return thumbnails and video etc. Facebook will have a seprate service provider for itself. Other than these specific service providers, we also have general service providers such as embed.ly which which serve for multiple sources.

So a person should be able to tell what provider to use if he has multiple options. How does one tell is obviously by using tags, **drupal-url**
, so by using a method called process_text we filter out that tag, and pass the url and optionally the configuration options to the embed library.
replace the **drupal-url**  by a div tag and put in the data in it.

Though i have written the filter, i am still getting a stray drupal render_array bug, which is a bug i need to resolve, the issue has now been raised, in [drupal issue queue](https://www.drupal.org/project/issues/url_embed "issue-queue"), I will update the blog as and when that gets resolved.

plus you can now follow the code at my [github](https://github.com/prateekmehta/url_embed) account too.

[url-embed-issues]: [url-embed-gh]:


[jekyll]:      http://jekyllrb.com
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-help]: https://github.com/jekyll/jekyll-help
