---
comments: true
date: 2011-11-14 22:21:23
layout: post
slug: arrow-keys-dont-work-properly-in-totalview-debugger
title: Arrow keys  don't work properly in Totalview Debugger
wordpress_id: 279
categories:
- C/C++
- Linux
tags:
- Debug
- tips
- Totalview
---

Totalview is a very powerful debugger for C/C++, Fortran languages, especially for debugging high performance programs. In this commandline interface(a new xterm window) no matter how hard I tried my arrow 'Up' key entered [[A char and 'Down' keys gave [[B char. What I really wanted was the 'history-previous' and 'history-next' in common Bash terminals. This type of malfunction really sucks when you debug a program through CLI. I thought at the beginning that it was due to curtain 'mismatch' between different 'TERM's or xterm mis-configuration. Wired, arrow keys worked fine if I myself started xterm. I have tried many so-called key remap configurations for xterm, rxvt or vt100/102. None of them worked.

Finally I realized that Totalview heavily relies on TCL. Its CLI is also built from TCL. So when I ran 'tclsh' in my Gnome terminal, pressing arrow keys misbehaved the exactly same way as in Totalview CLI. Therefore I continued the solution search online until I found [http://utopia.knoware.nl/~hlub/rlwrap/](http://utopia.knoware.nl/~hlub/rlwrap/). Simply run 'rlwrap tclsh' and 'rlwrap tv8cli' and the arrow keys worked like a charm.

I further aliased 'tv8cli' as 'rlwrap tv8cli'. But I still couldn't make it work in Totalview's GUI xterm CLI. Is there a way to do that?
