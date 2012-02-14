---
layout: post
title: How to install MongoDB on Ubuntu 11.10
description: How to install the MongoDB document store on Ubuntu 11.10 Oneiric.
tags: [mongodb ubuntu]
---

10gen publishes MongoDB packages, here is how to install one.

Add the 10gen repo to your source list.

{% highlight bash %}
	$ sudo gedit /etc/apt/sources.list
{% endhighlight %}

*/etc/apt/sources.list*

{% highlight bash %}
	...
	deb http://extras.ubuntu.com/ubuntu oneiric main
	deb-src http://extras.ubuntu.com/ubuntu oneiric main

	deb http://downloads-distro.mongodb.org/repo/ubuntu-upstart dist 10gen
{% endhighlight %}

Add the GPG key

{% highlight bash %}
	$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv 7F0CEB10
{% endhighlight %}

Update your packakes list.

{% highlight bash %}
	$ sudo apt-get update
{% endhighlight %}

Install the MongoDB package.

{% highlight bash %}
	$ sudo apt-get install mongodb-10gen
{% endhighlight %}

Check that it is working by entering:

{% highlight bash %}
	$ mongo
{% endhighlight %}

You should now see this:

{% highlight bash %}
	MongoDB shell version: 2.0.2
	connecting to: test
	> 
{% endhighlight %}

