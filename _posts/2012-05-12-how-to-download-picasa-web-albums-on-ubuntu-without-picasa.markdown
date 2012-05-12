---
layout: post
title: How to download Picasa web albums on Ubuntu without Picasa
description: How to download Picasa web albums on Ubuntu without Picasa
tags: [photos picasa ubuntu]
---

I use Picasa web albums mainly as a backup system, i didn't really care about nor use the Linux Picasa version
except to upload to and download from Picasa web albums. Well our Google overlords have recently decided to pull
the plug on the linux version so we are left with incomplete (Shotwell), complicated (Conduit), or shitty (Digikam) solutions.
Well uploading to Picasa web albums is covered by Shotwell but for downloading it turns out that there is a quick and
easy way to do it.

Install the [DownThemAll](https://addons.mozilla.org/en-US/firefox/addon/downthemall/) Firefox extension.

Now log into your Picasa account, click on an album that you want to download and on the album page click on the
Rss link on the right. Once on the Rss page click in the adress bar and add "&imgmax=d" (without quotes) to the
end of the url, reload the page. This will ensure downloaded images have their original sizes.

Now right click on the page, select DownThemAll, select the Links tab (and not Pictures and media, those are the thumbnails)
make sure the JPEG images is ticked in the Filters section, choose your destination folder and click Start.


