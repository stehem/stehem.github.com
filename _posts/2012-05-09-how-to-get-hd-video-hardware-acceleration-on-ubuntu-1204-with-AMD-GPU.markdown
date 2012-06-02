---
layout: post
title: How to get HD video hardware acceleration on Ubuntu 12.04 with AMD GPUs
description: HHow to install Ruby with rbenv on Ubuntu 12.04
tags: [xbmc ubuntu]
---

It used to be a major pain in the ass to enable hardware x264 decoding on Ubuntu, unfortunately if you have
a netbook or low powered laptop it is mandatory for watching HD content in good conditions. Until very recently
you had to mess with VAAPI, that meant hunting down custom xvba and libva libraries, which you painfully installed
and then locked down. And then you had to compile mplayer with VAAPI support, VLC has VAAPI support built in but
performance is poor, playback is not smooth. Then there was XBMC with VAAPI support, great performance, as good as
mplayer but without needing to compile and with a great GUI. Still had to suffer through VAAPI installs.
Now that there is a version of XBMC with xvba baked in, it is possible to get perfect, accelerated HD playback with an AMD GPU without the VAAPI nonsense, you just need
the proprietary fglrx drivers, it is quick, easy and almost painless. 

Start by installing fgrlx drivers if you do not have them already.
{% highlight bash %}
$ sudo apt-get install fglrx fglrx-amdcccle
$ sudo aticonfig --initial
{% endhighlight %}

All the info and credit comes from and goes to [this thread](http://forum.xbmc.org/showthread.php?tid=116996), that being
said you do not need all the steps, in fact you do not need most of them but you do need an extra one.

Add the XBMC repository to your system, but do not install XBMC yet, contrary to what the thread suggests if you just sudo apt-get
install xbmc you will get the vanilla vaapi Eden in the official repository, we do not want that.

{% highlight bash %}
$ sudo add-apt-repository ppa:wsnipex/xbmc-xvba
$ sudo apt-get update
{% endhighlight %}

Find the name of the xvba version we want to install:
{% highlight bash %}
$ apt-cache madison xbmc
$ apt-cache madison xbmc-bin
{% endhighlight %}
The version names we want are on lines ending with "Packages" and containing the xbmc-xvba ppa.

Install xbmc:
{% highlight bash %}
$ sudo apt-get install xbmc=COPY_HERE_THE_VERSION_NAME_FOR_XBMC xbmc-bin=COPY_HERE_THE_VERSION_NAME_FOR_XBMC-BIN
{% endhighlight %}

Example *sudo apt-get install xbmc=2:12.0~git20120502.1900-e9e0027-0precise xbmc-bin=2:12.0~git20120502.1900-e9e0027-0precise*

Now just make sure xvba is selected in the Video Playback XBMC menu, enable TearFree in the Catalyst drivers or set the vsync options
to prevent tearing and enjoy sweet, sweet HD hardware decoding.

Big bonus, you can use XBMC to accelerate YouTube Flash HD videos, just use the built in YouTube plugin to watch videos.

