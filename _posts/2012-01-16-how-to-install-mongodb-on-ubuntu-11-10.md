---
layout: post
title: How to install MongoDB on Ubuntu 11.10
description: How to install the MongoDB document store on Ubuntu 11.10 Oneiric.
tags: [mongodb ubuntu]
---

10gen publishes MongoDB packages, here is how to install one.

Add the 10gen repo to your source list.

<pre class="prettyprint" style="padding-bottom:15px;"> 
	<span class="nocode">
	$ sudo gedit /etc/apt/sources.list
	</span>
</pre>

*/etc/apt/sources.list*

<pre class="prettyprint" style="padding-bottom:15px;"> 
	<span class="nocode">
	...
	<em>deb http://extras.ubuntu.com/ubuntu oneiric main</em>
	<em>deb-src http://extras.ubuntu.com/ubuntu oneiric main</em>

	deb http://downloads-distro.mongodb.org/repo/ubuntu-upstart dist 10gen
	</span>
</pre>

Add the GPG key

<pre class="prettyprint" style="padding-bottom:15px;"> 
	<span class="nocode">
	$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv 7F0CEB10
	</span>
</pre>

Update your packakes list.

<pre class="prettyprint" style="padding-bottom:15px;"> 
	<span class="nocode">
	$ sudo apt-get update
	</span>
</pre>

Install the MongoDB package.

<pre class="prettyprint" style="padding-bottom:15px;"> 
	<span class="nocode">
	$ sudo apt-get install mongodb-10gen
	</span>
</pre>

Check that it is working by entering:

<pre class="prettyprint" style="padding-bottom:15px;"> 
	<span class="nocode">
	$ mongo
	</span>
</pre>

You should now see this:

<pre class="prettyprint" style="padding-bottom:15px;"> 
	<span class="nocode">
	MongoDB shell version: 2.0.2
	connecting to: test
	> 
	</span>
</pre>

