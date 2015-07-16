---
layout: post
title:  "Text Filter & Url Buttons"
date:   2015-07-1 22:40:00
categories: Gsoc'15 updates
tags: featured
image: /assets/article_images/2014-08-29-welcome-to-jekyll/desktop.jpg
---
Its been a while since i had last written a blog post on the work done so far, and i am not very proud of it. I will try and keep you guys updated about the work from now on.

So till last blog i had mentioned about Omembed Providers, and talked how text filters are used to replace certain placeholders in a page by the content of the url. If i have not mentioned it earlier, we are using Embed library for this. What we are exactly is that we go through the text extract the value for variable drupal-data-url, pass it to the Embed library, which uses certain providers, and return to us the content of that page,for example, if we provide it a youtube's video's url it will return to us the iframe of that video, which will fill the placeholder for the tag.

Apart from the text filter i have also been working on Url Buttons, this is basically a form which will allow a user to create several buttons lets say, one for the youtube, one for vimeo, one for twitter etc. By default it will be a genral button which will embed all/any url.

For adding a button in Drupal we first need to define its **schema**, which is kept in root's config\schema directory. The idea is that a button is defined by the value of these set of variables, which will be taken as input from a user, through a Url_button_form. In our case the schema is defined as :

{% highlight php %}

url_embed.url_button.\*:
  type: config_entity
  label: 'Url button config'
  mapping:
    label:
      type: label
      label: 'Name'
    id: 
      type: string
      label: 'Machine name'
    button_label:
      type: string
      label: 'Button label'
    source:
      type: string
      label: 'Source of Url'
    oembed_provider:
      type: string
      label: 'Oembed Provider'
    button_icon_uuid:
      type: string
      label: 'Button image'
    display_plugins:
      type: sequence
      label: 'Allowed display plugins'
      sequence:
        type: string
        label: 'Display plugin'

{% endhighlight %}

The **routing system** is responsible for matching paths to controllers, and you define those relations in routes.A route is a path which is defined for Drupal to return some sort of content on. For more information you can read more [here](https://www.drupal.org/developing/api/8/routing)

{% highlight php %}

url_button.list:
  path: '/admin/config/content/url-button'
  defaults:
    _entity_list: 'url_button'
    _title: 'Url Buttons'
  requirements:
    _permission: 'administer url buttons'

url_button.add:
  path: '/admin/config/content/url-button/add'
  defaults:
    _entity_form: 'url_button.add'
    _title: 'Add Url Button'
  requirements:
    _permission: 'administer url buttons'

entity.url_button.edit_form:
  path: '/admin/config/content/url-button/{url_button}'
  defaults:
    _entity_form: 'url_button.edit'
    _title: 'Edit Url button'
  requirements:
    _permission: 'administer url buttons'

entity.url_button.delete_form:
  path: '/admin/config/content/url-button/{url_button}/delete'
  defaults:
    _entity_form: 'url_button.delete'
    _title: 'Delete Url button'
  requirements:
    _permission: 'administer url buttons'

{% endhighlight %}

One we have the schema ready, we need to write the controllers now,  but before that we need to define the  buttons' interface which will be implemented by onew of the Form's class, braodly speaking this is nothing more than get and/or put the variable defined in the schema. We also need a class which will list all the buttons built in configurations/url_buttons.

Once the interface is implemented, we need to write the tests, just that you know, i have skipped on the source and provider "variables"  since we our library Embed doesn't make it possible for us to differentiate between them, It is an open issue on our Drupal.org issue que, if you have any inputs please comment there or leave me a message. Anyhow after writing the forms, I wrote a CRUD test, which is basically a create , update and delete test for the button. I have written the tests too, but overall this PR is still work in progress.

[drupal issue queue](https://www.drupal.org/project/issues/url_embed "issue-queue").

plus you can now follow the code at my [github](https://github.com/prateekmehta/url_embed) account.

[url-embed-issues]: [url-embed-gh]:


[jekyll]:      http://jekyllrb.com
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-help]: https://github.com/jekyll/jekyll-help
