---
layout: post
title:  "How to translate Mongoid model names"
date:   2015-03-08 17:15:00
author: odarriba
comments: true
categories: mongoid ruby-on-rails translation
---

If you worked with **MongoDB in a Ruby on Rails application**, you should have used a gem called [Mongoid][mongoid], which is a ODM (*Object Document Mapper*) that allows you to work with Mongo documents as native objects directly.

**Mongoid** models are very similar to *ActiveRecord*'s ones, but there is some tricky differences that can make your code more complex. **One of them is the translation of the model names**. 

Many gems use the *ActiveRecord* method `object.class_name.human` to obtain an **human-readable name of the model name**. This name is easy to translate in *ActiveRecord*, but when we switch to Mongoid, there is no documentation about where and how to translate these model names.
<!--more-->

In my degree's final project I've found this difficulty when I was coding an *extensible [CRUD][crud] user interface* in order to manage the models of my app. When I was doing the code that generates a table with results of searching objects, I was trying to use **only one translation file** for the texts in the table (which was going to be used with several different models), so I need to find the way to get the model name, and it should be translated.

To solve this, after finding in Internet, someone in [a blog][blog-solution] wrote about it and the solution was to **create a translation file** like similar to this, but in my case I've modified it to have singular and plural translations (this example is for `Service` model):

{% highlight yaml %}
en:
  mongoid:
    models:
      service:
        one: "service"
        other: "services"
  ui:
    table:
      results_of: "Results of %{entry_name}."
{% endhighlight %}

And in any other language (*spanish for example*), you should do it in the same way:

{% highlight yaml %}
es:
  mongoid:
    models:
      service:
        one: "servicio"
        other: "servicios"
  ui:
    table:
      results_of: "Resultados de %{entry_name}."
{% endhighlight %}

The last step is, obviously, use this translations in your application. A small example:

{% highlight ruby %}
@service = Service.where(:name => "The CodingCode service").first

flash[:info] = t("ui.table.results_of", :entry_name => @service.class_name.human(:count => 2))
{% endhighlight %}

After executing this 2 lines of code, the value of `flash[:info]`:

* Should be `Results of services` if the language used is **english**. 
* Should be `Resultados de servicios` if the language used is **spanish**.

Note that if we decide to use translations in the typical way, we should have specific translations for every model in which we use this translation. In this example case, the number of extra translations is the number of different models in which the CRUD interface will be used. 

Also, this kind of solutions makes your code **more reusable and extensible**, which is **a better code.**

[mongoid]: http://mongoid.org/
[crud]: http://en.wikipedia.org/wiki/Create,_read,_update_and_delete
[blog-solution]: http://www.frick-web.at/blog/rails-and-mongoid-i18n-model-attributes