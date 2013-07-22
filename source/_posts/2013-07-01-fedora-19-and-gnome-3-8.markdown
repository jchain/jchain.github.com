---
comments: true
layout: post
title: 'Fedora 19 and Gnome 3.8'
date: 2013-07-01 21:10:15
comments: true
categories: 
- Linux 
- Gnome
---

Last night I didn't resist the temptation to enter 

    sudo yum install fedora-upgrade 

Viola, my journey to Fedora 19 began!

Every time I upgraded my Linux to the latest release, either Ubuntu or Fedora, I would have to spent
another day to tweak the new system to make it comfortable to use. The biggest challenge was surely
the transition from GNOME2 to GNOME3. Two years have passed and I still can't get used to the new
UI. Accurately speaking, I really like the new UI elements in GNOME 3 but I just don't like the ways
that Gnome-shell asks me to do things. It is too obstrusive. It wanted to be smart but overdid. 

I appreciated the fallback mode that GNOME 3 provided. I turned off all the fancy animations and
sticked to the old-fashioned UI. I used [`tint2`][1] as the window list panel. In Fedora 18 with
Gnome 3.6, the clock applet surprisingly had a memory leak issue. I disabled the clock applet and
only used the `tint2` panel to show the time. However, sometimes, I missed the weather information.

With the advent of GNOME 3.8, the fallback was dropped and the 2D Gnome-Shell was so ugly that I had
to make a change. 

Thank God there is [`Cinnamon`][2]. Initially I thought of it as another flamboyant window manager
but it turns out the most faithful old pal. 

<!-- ![alt](https://dl.dropboxusercontent.com/u/309872/blog/2013-06-01-perlomni-in-vim.png) -->

[1]: http://code.google.com/p/tint2/
[1]: http://cinnamon.linuxmint.com/
