---
layout: post
title:  "Hello World!"
date:   2015-02-27 17:00:00
author: odarriba
comments: true
tags: blog
---
This is the first blog entry in this blog, **which aim is to share different problems and the source code of the solution** made.

My main idea is to write as the problems comes to me in my daily life. I'm currently developing a final project to complete my degree, so there are many problems to solve and I will try to post all of them as soon as they appear.

To start this blog in a developer way, I think that I should put this piece of code:

{% highlight ruby %}
#!/usr/bin/env ruby
def print_hello_world(name)
  puts "Hello world, #{name}!"
end

puts "What\'s your username?"
user_name = gets.chomp

print_hello_world(username)
#=> prints hello world to STDOUT.
{% endhighlight %}

<!--more-->

As you can see, my favourite programming language is **Ruby**, but I consider myself open-minded about it, and I don't reject to learn things about other modern technologies like *Node.js* or *AngularJS*, for example.

If you want to know a bit more about the author (me) yoy can visit the [About]({{% site.url %}}/about) page or you can leave a comment on this blog entry.

**See you soon!**