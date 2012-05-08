---
layout: post
title: How to install Ruby with rbenv on Ubuntu 12.04
description: HHow to install Ruby with rbenv on Ubuntu 12.04
tags: [ruby ubuntu]
---

So you got a clean 12.04 install or you are starting out with Ruby on Ubuntu, either way if you
just go ahead and follow the steps on the rbenv site it will fail on Ubuntu because we need to use
bashrc instead of bash_profile.


{% highlight bash %}
$ cd
$ git clone git://github.com/sstephenson/rbenv.git .rbenv
{% endhighlight %}

Here is where we need to stray from the rbenv site:

{% highlight bash %}
$ echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
{% endhighlight %}

Again

{% highlight bash %}
$ echo 'eval "$(rbenv init -)"' >> ~/.bashrc
{% endhighlight %}

Restart 

{% highlight bash %}
$ exec $SHELL
{% endhighlight %}

Now install ruby_build to easily install Ruby with rbenv

{% highlight bash %}
$ mkdir -p ~/.rbenv/plugins
$ cd ~/.rbenv/plugins
$ git clone git://github.com/sstephenson/ruby-build.git
{% endhighlight %}

Install Ruby

{% highlight bash %}
$ rbenv install 1.9.3-p185
{% endhighlight %}

You will have to rehash everytime you install a Ruby version or a gem

{% highlight bash %}
$ rbenv rehash
{% endhighlight %}

Make a Ruby version default:

{% highlight bash %}
rbenv global 1.9.3-p185
{% endhighlight %}

Test:

{% highlight bash %}
$ irb
irb(main):001:0> 
{% endhighlight %}
