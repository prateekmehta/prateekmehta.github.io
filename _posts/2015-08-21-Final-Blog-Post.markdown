---
layout: post
title:  "Concluding GSoC"
date:   2015-08-21 22:40:00
categories: Gsoc'15 updates
tags: featured
image: /assets/article_images/2014-08-29-welcome-to-jekyll/desktop.jpg
---

Hi all,

   So finally this GSoc ends, and we managed to almost acheive what we planned, a working module for embeding URL in WYSIWIG editor. I would like this post to be a walk through the different development stages, a sort of summary of the entire work cycle so a user who would want to build similar module can go through this blog and get a brief if not detailed idea of how this module was developed and for more details they can refer to the previous blogs in the series. I will conclude this blog by stating future goals for this module.

   First things first, how to get started with Drupal :
   So this journey started by walking through the [Drupal GSoC page](https://groups.drupal.org/google-summer-code), and always being online on Drupal's IRC Channel "drupal-google". where I got to know about Drupal ladder, for any new student the first task will be to complete Drupal Ladder, followed by contributing to Drupal, start from Novice issues, initially it may look like you are not learning much by simply changing spelling errors or something, but this is very important and you will learn the most important thing of all, how to connect to the community. I would like to emphasize that the most important thing i learnt through out this summer was how to  leaverage Drupal's huge community and ofcourse  helping back, where ever possible.

   Now coming back to the module, so this module started by defining what we wanted, so what we wanted was an easier way to render a URL, embedding its content in our case. We found out concept of Oembed and Oembed providers. We then found out about Embed Library, and decided that we will let Oscar Otereo's Embed do the heavy stuff for us, i.e. given a URL, it fetches Embed Code for us, provided it supports that source, in later stages we might look forward to add adapters, but that is an idea that needs to be explored. 

  Further more, once that was decided, we moved forward to Filters, or processing text, simply put, we scan for a div which indicates that there is  a URL a users intends to embed, we look for that URL, pass it to Embed, which internally send request to its registered provider, fetches embed code and returns it to us, we replace that Node in the HTML by that code and voila! we have our Embeded URL.
  
  Moving forward we wanted this to happen, using Buttons, URL Button as we call it, initially we wanted a seprate URL for different sources, say youtube will have a Button and Vimeo will have its seprate button, but that would require that Embed should ask for a provider or source as seprate argument, but that was unfortunately not the case, or we could check the provider name in the returned json by Embed, and put a condition on Source Provider from our end, or we could change the library to something else which provides us that, what is the best way to do it is still an [open issue](https://www.drupal.org/node/2529318), feel free to contibute in the url embed [issue queue](https://www.drupal.org/project/issues/url_embed). Nevertheless we moved forward, with just one universal button for all sourcep provider, but we left a form which allows a user to add more buttons, once we have a solution to that we will add fields specific to provider and source.

  Next we had was [CKeditor Integration](http://prateekmehta.github.io/gsoc'15/updates/2015/08/07/Ckeditor-Integration.html), which involved using a Dialog Form which asks for a URL and embed it once a user clicks on the URL Button, or the URL Embed Button as we now call it, this was intended so a user doesn't have to write in sort of a detailed markup language and could do it unsing UI, this was the fairly recent blog, so I am not writing in detail on it, this involves javascript which opens a dialog form in a separate dialog box, asks for a url, and pass it to a script which does the same thing which essentially we did with Text Filters.Here too we wrote a script which runs all the enabled filters in the CKeditor and returns the result.

  Next up we had was [Formatter](http://prateekmehta.github.io/gsoc'15/updates/2015/08/07/Ckeditor-Integration.html), so Embeding a URL is not the only way to render a URL, other ways such as using Title of of the URL's content etc already exist for "link" type of field our task was to add another field Formatter which would embed that url, as usual this task was also done by making a seprate plugin for this task, in my prevous [blog](http://prateekmehta.github.io/gsoc'15/updates/2015/08/07/Ckeditor-Integration.html) I have already mentioned useful tutoriols and link to the github code.

  Finally I would like to direct you guys to url embed issue queue, link given below, to have a look at it and contribute, test and report bugs.In future we have two major tasks still pending, 
  1) we are still relying on  flickr for our testing, we need to create our own testing module, problems related to that are there in my [previous blogs](http://prateekmehta.github.io/gsoc'15/updates/2015/08/01/Blog-Post.html) as well as the issue queue in issue number [2534170](https://www.drupal.org/node/2534170).
  2) restrain on source providers and sources, issue number [2529318](https://www.drupal.org/node/2529318)

  I will keep on maintianing the code for atleast another year, so kindly feel free to contact me as and when requred, also any major/minor annoucements shall also take place through this blog only so if you are keen on followign up, please subsribe to this blog, till then ADIOS!



[drupal issue queue](https://www.drupal.org/project/issues/url_embed "issue-queue").

plus you can now follow the code at drupal media's  [github](https://github.com/drupal-media/url_embed) account.

[url-embed-issues]: https://github.com/drupal-media/url_embed 
[url-embed-gh]: https://github.com/drupal-media/url_embed


[jekyll]:      http://jekyllrb.com
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-help]: https://github.com/jekyll/jekyll-help
