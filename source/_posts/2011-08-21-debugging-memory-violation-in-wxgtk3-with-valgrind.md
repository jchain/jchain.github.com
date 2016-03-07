---
comments: true
date: 2011-08-21 16:30:39
layout: post
slug: debugging-memory-violation-in-wxgtk3-with-valgrind
title: Debugging memory violation in wxgtk3 with valgrind
wordpress_id: 229
categories:
- C/C++
- Linux
tags:
- C/C++
- GDB
- Valgrind
- wxWidgets
---

wxgtk3 is under active development. Today I ran into a **SIGABRT** signal when debugging samples/image. The error message is like this:


> *** glibc detected *** ./image: malloc(): smallbin double linked list corrupted: 0x0000000000c93180 ***
======= Backtrace: =========
/lib64/libc.so.6(+0x73226)[0x7f580b58f226]
/lib64/libc.so.6(+0x758cf)[0x7f580b5918cf]
/lib64/libc.so.6(__libc_malloc+0x79)[0x7f580b593aa9]
/usr/lib64/libstdc++.so.6(_Znwm+0x1d)[0x7f580bd6d3dd]
/usr/lib64/libstdc++.so.6(_Znam+0x9)[0x7f580bd6d4f9]
./image[0x4a6d2c]
./image[0x4a8d7c]
./image[0x4ab21f]
./image[0x4aaeb6]


What is "_malloc(): smallbin double linked list corrupted_" error? I had no clue. I loaded the program in gdb and saw this error happens when a specific line of code having 'new' operator was hit. It should be some memory allocation violation. I searched it in Google. The returned results showed many bug reports containing this error. Interestingly, a good number of the follow-up replies said the bug was not reproducible and suggested the original  bug reporter submit valgrind log but few did that so these bug reports were marked as invalid.

I guessed most bug reporters were just common users who were not familiar with valgrind. Anyway, the search results suggested me run valgrind to get more information about the memory violation. Luckly, I played with it several month ago and made a not-bad [suppression file](http://zandyware.wordpress.com/2011/01/21/share-my-newly-created-valgrind-wxgtk-2-9-1-suppression-file/) customized with wxgtk. Again I ran valgrind with the command like this:

G_SLICE=always-malloc G_DEBUG=gc-friendly valgrind --leak-check=yes --suppressions=./wx.supp --log-file=valgrind.log ./image

Valgrind immediately tracked down where the real problem was. The log looked like this


> ==17645== Memcheck, a memory error detector
==17645== Copyright (C) 2002-2010, and GNU GPL'd, by Julian Seward et al.
==17645== Using Valgrind-3.6.1 and LibVEX; rerun with -h for copyright info
==17645== Command: ./image
==17645== Parent PID: 28951
==17645==
==17645== Source and destination overlap in memcpy(0xe004860, 0xe003430, 5600)
==17645==    at 0x4C289A6: memcpy (mc_replace_strmem.c:635)
==17645==    by 0x447DD0: wxBitmap::CreateFromImageAsPixmap(wxImage const&, int) (bitmap_gtk3.cpp:500)
==17645==    by 0x447910: wxBitmap::CreateFromImage(wxImage const&, int) (bitmap_gtk3.cpp:383)
==17645==    by 0x425694: wxBitmap::wxBitmap(wxImage const&, int) (bitmap.h:72)
==17645==    by 0x42DDEA: MyCanvas::MyCanvas(wxWindow*, int, wxPoint const&, wxSize const&) (canvas.cpp:199)
==17645==    by 0x41EE7F: MyFrame::MyFrame() (image.cpp:678)
==17645==    by 0x420B23: MyApp::OnInit() (image.cpp:878)
==17645==    by 0x424A22: wxAppConsoleBase::CallOnInit() (app.h:92)
==17645==    by 0x611002: wxEntry(int&, wchar_t**) (init.cpp:456)
==17645==    by 0x6110F1: wxEntry(int&, char**) (init.cpp:484)
==17645==    by 0x420A84: main (image.cpp:869)
==17645==
==17645== Invalid read of size 8
==17645==    at 0x4C28B2C: memcpy (mc_replace_strmem.c:635)
==17645==    by 0x447DD0: wxBitmap::CreateFromImageAsPixmap(wxImage const&, int) (bitmap_gtk3.cpp:500)
==17645==    by 0x447910: wxBitmap::CreateFromImage(wxImage const&, int) (bitmap_gtk3.cpp:383)
==17645==    by 0x425694: wxBitmap::wxBitmap(wxImage const&, int) (bitmap.h:72)
==17645==    by 0x42DDEA: MyCanvas::MyCanvas(wxWindow*, int, wxPoint const&, wxSize const&) (canvas.cpp:199)
==17645==    by 0x41EE7F: MyFrame::MyFrame() (image.cpp:678)
==17645==    by 0x420B23: MyApp::OnInit() (image.cpp:878)
==17645==    by 0x424A22: wxAppConsoleBase::CallOnInit() (app.h:92)
==17645==    by 0x611002: wxEntry(int&, wchar_t**) (init.cpp:456)
==17645==    by 0x6110F1: wxEntry(int&, char**) (init.cpp:484)
==17645==    by 0x420A84: main (image.cpp:869)


It turned out that memcpy() at the line 500 in bitmap_gtk3.cpp manipulated overlapping memory. That was the actual culprit. Valgrind even showed the call backtrace to help you to reproduce the bug. Awesome.

I hope this blog entry help you to use Valgrind to locate the bug and fix memory error quickly.
