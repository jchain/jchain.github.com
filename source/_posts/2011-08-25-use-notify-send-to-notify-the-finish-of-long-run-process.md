---
comments: true
date: 2011-08-25 20:21:46
layout: post
slug: use-notify-send-to-notify-the-finish-of-long-run-process
title: Use notify-send to notify the finish of long run process
wordpress_id: 231
categories:
- Linux
tags:
- Linux
- tips
---

This Linux executable is part of the package 'libnotify'. With it you can notify the finish of long run process, like


> ./LongRunProcess | notify-send Done "LongRunProcess is done"
