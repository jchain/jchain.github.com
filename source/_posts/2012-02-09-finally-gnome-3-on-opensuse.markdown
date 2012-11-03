---
comments: true
date: 2012-02-09 17:08:38
layout: post
slug: finally-gnome-3-on-opensuse
title: Finally Gnome 3 on openSUSE
wordpress_id: 343
categories:
- Linux
tags:
- GNOME
- Linux
- openSUSE
---

After upgrading from openSUSE-11.4 to 12.1, I have spent two days on tweaking GNOME3 to make it usable. Phew.

Initially, GNOME3 (gnome-shell 3.2 precisely) was unable to start at all. .xsession-errors showed that Clutter failed to start. A deeper reason was that Clutter wasn't able to find the proper nVidia graphics driver libGL*.so. If you type

[sourcecode language="bash"]

ldd /usr/bin/gnome-shell

[/sourcecode]

You would notice that libGL.so.1 was pointing to nothing. That was bad.

I narrowed down the culprit in my .bashrc. For some reason I have always modified LD_LIBRARY_PATH to meet my needs. Everything worked fine until upgrade to openSUSE-12.1. I found from /etc/ld.conf.d that the nVidia GL libraries had been installed in /usr/X11R6/lib64 and /usr/X11R6/lib which was missed in my modified LD_LIBRARY_PATH. So the solution was to add /usr/X11R6/lib64:/usr/X11R6/lib in the front of LD_LIBRARY_PATH. It seemed to have to be the first two in my case. YMMV. I didn't run into the same problem on Ubuntu since the nVidia driver was installed somewhere else.

OK. Gnome shell started but soon I noticed that there was some screen refresh glitches in gnome-terminal. Every time I typed commands where the cursor was near the bottom, the screen failed to refresh or output.  I hadn't seen it in KDE running the same program. So I guess it again was related with Gnome-shell. A quick search on the web told me that it was due to some bugs in nVidia driver with Clutter and  the work around was to add the following line into .bashrc

[sourcecode language="bash"]

export CLUTTER_PAINT=disable-clipped-redraws:disable-culling

[/sourcecode]

Again I didn't run into this issue in Ubuntu.

All right. Gnome-terminal worked properly. After further installs of Gnome shell extensions like Application Menu, Places Status Indicator, and [tint2](http://code.google.com/p/tint2/), finally my new GNOM 3 was ready for daily use.
