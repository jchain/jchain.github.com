---
comments: true
date: 2010-04-24 05:33:50
layout: post
slug: do-you-want-to-debug-a-program-with-command-line-parameters-in-visual-c-2008
title: Do you want to debug a program with command line parameters in Visual C++ 2008?
wordpress_id: 24
tags:
- C++
- Visual C++
---

Set them in project->configuration properties->Debugging. But there is one more thing to do: Set your project as the Startup Project in the Solution Explorer! If you don't do that, the command line parameters won't be passed in whatever you try!
