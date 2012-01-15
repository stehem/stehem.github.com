---
layout: post
title: How to use the flash with express.js
description: How to easily implement the flash notification system with the Express.js Node Framework.
tags: [express]
---

If you have used Ruby On Rails you probably know and appreciate the flash notification system, here is how
you can more or less have the same thing with Express.

Register a dynamic helper In *app.js* or your equivalent:

<pre class="prettyprint" style="padding-bottom:15px;"> 
	app.configure(function(){
	//...
		app.dynamicHelpers({flash: function(req, res){return req.flash();}});
	});
</pre>

Add to the flash object where needed:

<pre class="prettyprint" style="padding-bottom:15px;"> 
	app.post('/new_user', function(req, res){
		//..
		req.flash('notice', "Account successfully created.");
	});
</pre>

And finally in your view, a *Jade* template in this case:

<pre class="prettyprint" style="padding-bottom:15px;"> 
	if typeof flash != 'undefined' && flash.notice
		!= flash.notice
</pre>

And that's it. Hope it helps someone out.

