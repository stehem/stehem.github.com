---
layout: post
title: How to get Pygments to work with Jekyll
description: How to get pygments to work with Jekyll
tags: [jekyll pygments]
---

At first getting Pygments to do syntax highlighting with Jekyll seems pretty straightforward if one glances at the various
tutorials, there is basically nothing to do. In my case Pygments was not working with Jekyll, here is what i did to get it to
work and achieve some very nice syntax highlighting. By the way if you are using Bootstrap, as i was, using Pygments is much
nicer than the Prettify Google javascript library that Bootstrap suggests using...

So, install Pygments and make sure that it is enabled in *_config.yaml*

On Ubuntu
{% highlight bash %}
$ sudo apt-get install python-pygments
{% endhighlight %}

In *_config.yaml*
{% highlight yaml %}
pygments: true
{% endhighlight %}

And the last step that was necessary in my case, but that none of the articles popping up on Google mentioned, manually generating
the css file needed for color highlighting. 
{% highlight bash %}
$ cd path/to/jekyll/project/folder
$ pygmentize -S default -f html > stylesheets/pygments.css
{% endhighlight %}

Now you just have to include the generated css file in your layout.

Bonus: if you use Twitter Bootstrap, you need an extra step because Bootstrap's styles will conflict and mees up our hard-earned sweet
syntax highlighting.

Locate this line in *bootstrap.min.css*
{% highlight css %}
code{background-color:#fee9cc;color:rgba(0, 0, 0, 0.75);padding:1px 3px;}
{% endhighlight %}

And replace it with:
{% highlight css %}
code{color:rgba(0, 0, 0, 0.75);padding:1px 3px;}
{% endhighlight %}

