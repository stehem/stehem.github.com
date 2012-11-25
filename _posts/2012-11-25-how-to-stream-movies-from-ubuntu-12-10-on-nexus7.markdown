---
layout: post
title: How to stream movies from an Ubuntu 12.10 box on a Nexus 7 tablet
description: How to stream things from Ubuntu on Android.
tags: [samba android]
---

So, you have a Nexus 7 or any Android based device and you quickly come to realise that transferring files from Ubuntu to your Nexus 7 is
a pain in the ass, MTP support isn't included in 12.10 and gMTP is a buggy piece of, well, you can try to install mtp libs and auto mount
the tablet to use with Nautilus but that does not work well and isn't very convenient anyway. What if you could directly stream the file
without messing with cables and transferring?

To do that we will use Samba on Ubuntu and ES File Explorer on Android.

Let's install Samba.
{% highlight bash %}
$ sudo apt-get install samba
{% endhighlight %}

Now we need to configure some things:

{% highlight bash %}
$ sudo gedit /etc/samba/smb.conf 
{% endhighlight %}

Locate this line...

{% highlight bash %}
# security = user
{% endhighlight %}

...and uncomment it by removing the #

Locate those two lines...

{% highlight bash %}
SO_RCVBUF=8192 SO_SNDBUF=8192
socket options = TCP_NODELAY
{% endhighlight %}

...and uncomment them as well, this made the setup smooth as butter.

Now, at the bottom of the file append those lines:

Modify the path line with the path to the directory containing your movies:
{% highlight bash %}
[Movies]
	path = PATH-TO-THE-FOLDER-YOU-WANT-TO-SHARE
	writeable = no
	browseable = yes
	guest ok = yes
{% endhighlight %}

Save the file and close it.

Create a password for Samba:
{% highlight bash %}
$ sudo smbpasswd -a YOUR-USERNAME
{% endhighlight %}


{% highlight bash %}
$ sudo restart smbd
$ sudo restart nmbd
{% endhighlight %}

Done on the Ubuntu front, now on Android.

Install ES File Explorer from the Play Store.

Launch it, on the top left corner change from Local to Lan.

Click on the Search icon.

If all goes well and your tablet and computer are on the same wifi network your computer should appear.

Long press the computer icon and select Edit Server, uncheck Anonymous and enter your username (the one you used for the sudo smbpasswd -a command)
and the password you created at the same step.

Click OK.

Now you can browse your files, in my case i use BS Player and clicking on a movie file automatically launches it with BS Player.

Now you can enjoy the stuff on your Ubuntu computer with your Nexus 7 or other without messing with copying files around.

You should also activate buffering from the video player, in BS Player there is a buffering option in Preferences / Network.
The movie is a bit choppy on launch while it buffers but good afterwards.
