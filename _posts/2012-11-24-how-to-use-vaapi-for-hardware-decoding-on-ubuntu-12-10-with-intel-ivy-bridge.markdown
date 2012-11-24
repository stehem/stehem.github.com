---
layout: post
title: How to use vaapi for hardware video decoding on Ubuntu 12.10 with Intel Sandy/Ivy Bridge GPUs.
description: How to get hardware video acceleration with Intel HDx000 on Ubuntu 12.10
tags: [vaapi mplayer ubuntu]
---

You have HD3000 or HD4000 Intel integrated graphics so that means you can most likely decode HD 720p or even 1080p in software
mode but why not offload the video decoding to the GPU and watch your CPU use dwindle to almost nothing. It is very easy to do
on Ubuntu, here is how:

Install the Intel vaapi drivers
{% highlight bash %}
$ sudo apt-get install i965-va-driver
{% endhighlight %}

Now, to get a vaapi enabled mplayer, you can either grab the source from [here](http://gitorious.org/vaapi/mplayer) and build it
or much better grab a pre built package:
{% highlight bash %}
$ sudo add-apt-repository ppa:sander-vangrieken/vaapi
$ sudo apt-get update
$ sudo apt-get install mplayer-vaapi
{% endhighlight %}

Now to watch a movie with hardware decoding simply run this command:
{% highlight bash %}
$ mplayer -vo vaapi -va vaapi -fs -heartbeat-cmd "xscreensaver-command -deactivate" PATH-TO-MKV-FILE
{% endhighlight %}

There are many commands to use mplayer from the command lines, the most useful are:  
fullscreen toggle: f  
volume down/up: 9/0  
cycle through available subtitles: j  
toggle subtitles: v  
toggle OSD: O
skip forward/backward: right or up arrow / left or down arrow 
