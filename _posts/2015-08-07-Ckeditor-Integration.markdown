---
layout: post
title:  "Ckeditor Integration and Field Formatter"
date:   2015-08-07 22:40:00
categories: Gsoc'15 updates
tags: featured
image: /assets/article_images/2014-08-29-welcome-to-jekyll/desktop.jpg
---

Hi all,

A. Ckeditor Integration

   so these few days  were spent mostly working on Integrating our filters with CKditor. So in drupal 8 this is done by ckeditor plugin. so what we essentially wanted was instead of people writing a something like "<drupal-url> blah blah </drupal-url>" which is not a very convinient way, we wanted to present an end user a button "Url Button" which we have discussed in previous blogs.

   So a user when clicks on a Button should get a Form, we call it an Embed Form, which essentially asks a user required information such as very obvious, what url you want to embed, and for later stages may be what source providers if any you would want to choose or how you may want your embeded media to look like say if you have multiple thumnails availaible and things like that. But For the time being we restricted ourselves to very basi and functional form which simply asks for the URL an end user wants to embed.

   Now this is done with the help of a javascript which you can have a look at the github [here](https://github.com/drupal-media/url_embed/blob/8.x-1.x/js/plugins/drupalurl/plugin.js). It basically opens a Dialog box present the [EmbedDialog Form](https://github.com/drupal-media/url_embed/blob/8.x-1.x/src/Form/UrlButtonForm.php) and passes input to Embed Controller which returns the Ajax response to return preview of the URL, by running thr text filters we have already inplemented durin g "Text Processing"
   
   Given below are some snapshots of the dialog form and some other snapshots from our module.

B. Field Formatter.
      
   Another thing i have been working on is a field formatter, field formatter tell us how a field type will be displayed, since we are working on embeding URLs so obviously we added a formatter for a "Link" type of field which is nothing but a way to add URLs . Since we were working on Embedding a URL, we made a formatter which takes input from that field ie a URL passes that URL to the Embed Library and gets the embed code, and renders the URL as that Embeded media instead of showing Title or using that URL as a tittle,(such formatters were already availaible in drupal). As usual field formatters are also implemented as plugins in drupal 8, you can have a look at how we implemented a formatter for link type field called LinkEmbedFormatter [here](https://github.com/prateekmehta/url_embed/blob/6fd0684d8a15643cff4d22dd98fb30ba60d507bf/src/Plugin/Field/FieldFormatter/LinkEmbedFormatter.php) it is still in a PR, a test is still pending for this which i will complete, very soon. This tutoriol here was veryhelpful, so if you want implement a formatter yourself, [this](http://enzolutions.com/articles/2014/12/09/how-to-create-a-field-formatter-in-drupal-8/) should be good start.

   One interesting thing i learnt while building formatters, which i find worth sharing is about fallback formatters, so this issue cam up offcourse, when we thought what happend if Embed fails to return the code, so it was very intutive to put it in a try-catch block but interestingly o was asked not to log such errors like we did during Text Filters, why so ? because it turned out drupal has this option of fall back formatters ie all formatters try to format that  particular field and one which is succesfully formats it and is higher on priority is used.



[drupal issue queue](https://www.drupal.org/project/issues/url_embed "issue-queue").

plus you can now follow the code at my [github](https://github.com/prateekmehta/url_embed) account.

[url-embed-issues]: [url-embed-gh]:


[jekyll]:      http://jekyllrb.com
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-help]: https://github.com/jekyll/jekyll-help
