---
comments: true
date: 2011-01-21 20:34:21
layout: post
slug: share-my-newly-created-valgrind-wxgtk-2-9-1-suppression-file
title: Share my newly created Valgrind wxGTK-2.9.1 suppression file
wordpress_id: 99
categories:
- C/C++
- wxWidgets
tags:
- C/C++
- Debugging
- tips
- Valgrind
- wxWidgets
---

If you want use Valgrind to check the memory leak of your wxGTK program, you probably end up with
too many false detections. You need a suppression file to help you focus on the real problem you are
dealing with. I followed the great article at[
http://wiki.wxwidgets.org/Valgrind_Suppression_File_Howto](http://wiki.wxwidgets.org/Valgrind_Suppression_File_Howto)
to create my first wxGTK suppression file. The version of wxGTK is 2.9.1 and my OS is openSUSE-11.1
**x86-64** . If your OS arch is not x86-64, you may need to modify the string occurrences  '64'  in
suppression file. I tested my suppression file with wxWdgets sample program 'mininal' the error
number is 2, with sample opengl program 'cube' the error number is 0. I hope I didn't overact in my
suppression file.

I suggested using the following command to fire up valgrind:

    G_SLICE=always-malloc G_DEBUG=gc-friendly valgrind --leak-check=yes
    --suppressions=./wx.supp --log-file=valgrind.log ./YOUR_PROG

Download it at here [wx.supp](http://zandyware.files.wordpress.com/2011/01/wx-supp.doc). And
**remove the 'doc' extension or rename to whatever you like since it is a plain txt file per se.**

Read more at [http://live.gnome.org/Valgrind ](http://live.gnome.org/Valgrind)
