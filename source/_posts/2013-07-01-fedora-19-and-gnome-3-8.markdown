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
the transition from GNOME 2 to 3. Two years have passed and I still can't get used to the new UI.
Accurately speaking, I really like the new UI elements in GNOME 3 but I just don't like the ways
that GNOME shell asks me to do things. I think GNOME shell is attractive for new users and
especially good for tablet. But for a senior user, it is too obtrusive. It wanted to be smart but
overdid. 

I appreciated the fallback mode that GNOME 3 provided. I turned off all the fancy animations and
sticked to the old-fashioned UI. I used [`tint2`][1] as the window list panel. In Fedora 18 with
Gnome 3.6, the clock applet surprisingly had a memory leak issue. I disabled the clock applet and
only used the `tint2` panel to show the time. However, sometimes, I missed the weather information.

With the advent of GNOME 3.8, the fallback was sadly dropped and the 2D GNOME shell was so ugly that
I had to make a change. 

I first tried [`Xfce`][3] and `MATE Desktop`. `MATE` failed to start on my Fedora 19. I realized that
I was spoiled by the modern UI of GNOME 3 so the look and feel of `Xfce` (based on GTK+ 2) became
intolerable. Thank God there is [`Cinnamon`][2]. When Cinnamon was first released, I thought it was
another flamboyant window manager but it turns out sleek and practical. The status bar is very
compact but full of useful information. Window list? Check. Weather applet? Check. Start menu?
Check. Transparency effect? Check. GNOME compatible? Check. I don't need many. These are good
enough. I'm so happy to settle down with Cinnamon. 

Some other issues with GNOME 3.8 are

1. The transparency of the background of GNOME Terminal can't be set. Not a very big deal. But
   some users complained about it. 

2. The upgrade changed my wallpapers for the desktop and the GDM. I really wanted them to be
   kept.

3. The theme is broken. Many guys complain about [that][4] 

[1]: http://code.google.com/p/tint2/
[2]: http://cinnamon.linuxmint.com/
[3]: http://xfce.org
[4]: http://igurublog.wordpress.com/2012/11/05/gnome-et-al-rotting-in-threes/
