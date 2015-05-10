---
layout: post
title:  "How to cancel a setInterval in Javascript"
date:   2015-05-10 20:05:10
author: odarriba
comments: true
image: /assets/posts/javascript.png
tags: howto javascript setinterval
---

<img class='pull-right xs-size' src='/assets/posts/javascript.png' />
During the development of my degree final project, I had the necessity of cancel a previously set interval in Javascript. To anyone who doesn't know what this is, a `setInterval` operation allows the programmer set a period in which the task is executed. 

Searching a bit on the Internet I found a post in [StackOverflow](stackoverflow) that shows various possible options to cancel (or simulate a cancellation) of a `setInterval` operation, but the most correct one could be something like this:

{% highlight javascript %}
function myFunction() {
	// This returns an intervalID
	return setInterval(function(){
		doStuff();
	}, 1000);
}

var interval = myFunction();

// Do more stuff....

// Clear the interval
clearInterval(interval);
{% endhighlight %}

This `clearInterval(interval)` function is part of the basic JavaScript standard, implemented in most browsers and avoids the execution of the interval operation again.

There are other methods using flags, but these doesn't stop the interval forever (just returns from the operation without doing anything) so, in my opinion, this is the best way to do it.

[stackoverflow]: http://stackoverflow.com/questions/109086/stop-setinterval-call-in-javascript