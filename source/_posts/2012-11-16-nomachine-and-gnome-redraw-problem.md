---
layout: post
title: 'Nomachine and GNOME Redraw Problem'
date: 2012-11-16 15:36
comments: true
categories: 
- GNOME
---

I use [Nomachine][1] a lot when I work from home. My home and work Linux desktop are both running
GNOME 3. There were a problem disturbing me for a while. Everything works fine at workplace probably
due to the supper fast local internet connection. But when I connected to the remote desktop via
Nomachine, the GUIs of remote applications were very lagging and the redraws seemed out of sync
leaving blanks here and there. I've tried many ways to improve that, including upgrading the ISP
bandwidth, trying the latest NoMachine 4 Preview, tuning the various options in the settings. But
all efforts were vain. Until one day I aimlessly chose KDE in NoMachine and the redraw issue were
gone. Every GUI programs ran perfectly in KDE, both GTK+ ones and non-GTK+ ones.

[1]: http://www.nomachine.com
