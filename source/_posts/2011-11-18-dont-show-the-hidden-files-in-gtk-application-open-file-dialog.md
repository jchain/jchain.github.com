---
comments: true
date: 2011-11-18 07:55:05
layout: post
slug: dont-show-the-hidden-files-in-gtk-application-open-file-dialog
title: Don't show the hidden files in GTK+ application open file dialog
wordpress_id: 288
categories:
- Linux
tags:
- GNOME
- GTK
- Linux
---

It is quite annoying when you open a file selection dialog in a typical GTK+ application a pile of hidden files and directories occupy the window. **Solution:** edit ~/.config/gtk-2.0/gtkfilechooser.ini to disable the option 'ShowHidden'
