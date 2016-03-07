---
comments: true
date: 2010-12-21 20:06:02
layout: post
slug: how-to-install-openoffice-3-without-root-privilege
title: How to install OpenOffice 3 without root privilege
wordpress_id: 57
categories:
- Linux
tags:
- openoffice
- tips
- word processing
---

The default openoffice of my desktop Linux was aging and I just wanted to update to the latest
openoffice-3.2. But my problem was I didn't have the root privilege to do that. The official
installer of OpenOffice failed again over again without notifying you that the reason of failure was
the lack of root privilege. Finally I found this great
[post](http://www.oooforum.org/forum/viewtopic.phtml?t=26173). I followed what it said and it worked
like a charm. Only one thing I want to add: if you use color _ls_, use **ls --color=never** to
disable the color output.


  1. Download the installation package from OpenOffice website.
	
  2. Unzip it into a directory.
	
  3. **for i in `ls --color=never OOO320_m18_native_packed-1_en-US.9502/RPMS/*rpm`; do rpm2cpio $i | cpio -ivd; done**
	
  4. cd OOO320_m18_native_packed-1_en-US.9502/RPMS/opt/openoffice.org3/program/
	
  5. run ./soffice
	
  6. (option) create symbolic link to soffice.
	
  7. (option) set file association in Nautilus. Right click a doc and choose **Properties->Open with -> Add...**


