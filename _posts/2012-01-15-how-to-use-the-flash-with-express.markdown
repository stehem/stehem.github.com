---
layout: post
title: How to use the flash with express.js
description: How to easily implement the flash notification system with the Express.js Node Framework.
tags: [express]
---

If you have used Ruby On Rails you probably know and appreciate the flash notification system, here is how
you can more or less have the same thing with Express.

Register a dynamic helper In *app.js* or your equivalent:

{% highlight javascript %}
	app.configure(function(){
	//...
		app.dynamicHelpers({flash: function(req, res){return req.flash();}});
	});
{% endhighlight %}

Add to the flash object where needed:

{% highlight javascript %}
	app.post('/new_user', function(req, res){
		//..
		req.flash('notice', "Account successfully created.");
	});
{% endhighlight %}

And finally in your view, a *Jade* template in this case:

{% highlight javascript %}
	if typeof flash != 'undefined' && flash.notice
		!= flash.notice
{% endhighlight %}

And that's it. Hope it helps someone out.

