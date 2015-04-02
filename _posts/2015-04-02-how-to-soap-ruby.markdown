---
layout: post
title:  "How to create a SOAP client in Ruby"
date:   2015-04-02 20:56:00
author: odarriba
comments: true
image: /assets/posts/soap.jpg
tags: ruby soap client howto
---

<img class='pull-right sm-size' src='/assets/posts/soap.jpg' />
**SOAP** (*Simple Object Access Protocol*, [link][soap]) is a standard protocol that defines how we can make a communication between two objects of different processes using [XML][xml]. In other words, is a way of communicate with certain services using XML.

What I have to do is to create a client in Ruby to send petitions to a WCF (*Windows Communication Foundation*) application that uses SOAP. For this task I have researched a bit and I have found a Ruby gem called **Savon** ([link][savon-link]).

This gem allows you to initialize an object using certain configuration parameters and allowing you to send messages to the SOAP service, and read the response.

<!--more-->

## How do we use it?

First of all, you have to install the gem using `gem install savon --version '~> 2.0'`. After that, you can initialize a client object using code similar to this:

{% highlight ruby %}
# Check if Savon gem is installed
require("savon")

# Create the client
client = Savon.client(wsdl: 'http://...../?wsdl')
{% endhighlight %}

After this, we can access a lot of methods (described in the [gem documentation][savon-docs]), but a good approach can be doing a petitio to a service called `example` using something like this:

{% highlight ruby %}
response = client.call(:example, message: { foo: bar })
{% endhighlight %}

But if you, like me, have to call to a service using custom made objects of C#, your unique option is to use some WCF client (like the default included in *Visual Studio*) to examine the structure of the XML and clone it in the `message` section.

To read the response, you can access to the `response.body` object to obtain your data.

And remember, if you don't know how to do something, check the [documentation][savon-docs] or leave a comment!

[soap]: http://en.wikipedia.org/wiki/SOAP
[xml]: http://en.wikipedia.org/wiki/XML
[savon-link]: https://rubygems.org/gems/savon
[savon-docs]: http://savonrb.com/version2/