---
comments: true
date: 2011-03-03 07:48:26
layout: post
slug: built-gtk3-0-on-opensuse-11-1
title: Built gtk3.0 on openSUSE-11.1
wordpress_id: 145
categories:
- GNOME
tags:
- GTK
- Linux
---

I built gtk3.0 from source on openSUSE-11.1 x86-64bit. As expected, I ran into one annoying problem like this:


> symbol lookup error: /opt/gnome/lib/libcairo-gobject.so.2: undefined symbol: cairo_region_destroy


I searched for the solution online. Someone suggested disabling gobject-introspection when compiling gtk3. But the default setting for gtk3 is indeed without gobject-introspection support. I got stuck and very confused. Finally, I got the things done by compiling the latest gobject-introspection(0.10.x) and enabling gobject-introspection support for atk, gdk-pixbuf and any other dependency libraries which could be set to enable this feature. YMMV. Here is the screenshot showing the about dialog from gtk3-demo.

[caption id="attachment_147" align="aligncenter" width="432" caption="gtk3-demo"][![gtk3-demo](http://zandyware.files.wordpress.com/2011/03/gtk3-demo.png)](http://zandyware.files.wordpress.com/2011/03/gtk3-demo.png)[/caption]
