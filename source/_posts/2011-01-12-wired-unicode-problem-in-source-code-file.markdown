---
comments: true
date: 2011-01-12 22:27:22
layout: post
slug: wired-unicode-problem-in-source-code-file
title: Wired Unicode Problem in Source Code File
wordpress_id: 81
tags:
- C++
- text processing
- tips
---

Today I ran into a very wired problem when I was trying to compile a C++ source file. What I received was like this:


> Evaluator.h:1: error: stray ‘\357’ in program
Evaluator.h:1: error: stray ‘\273’ in program
Evaluator.h:1: error: stray ‘\277’ in program
Evaluator.h:1: error: stray ‘#’ in program


I googled this error and it turned out to be there were some invisible Unicode characters in the source file. I guessed that our team were using different editors and operating systems, and someone  accidentally inserted one or two unicode characters. It was so bad that they were invisible!

The first line was a comment so I deleted the whole line and retyped. But the build was still there! So so wired. I used Linux command-line tool 'file' to detect the type of the source file


> Evaluatore.h: UTF-8 Unicode (with BOM) C program text


But for the other files in the same directory, 'file' told me that


> ASCII C program text


Yes, I NEED ASCII file encoding! I tried gedit and iconv but somehow they both complained the conversion. So I came up the final idea, use command-line tool 'cat' to** dump it to the terminal screen** and copy whole content without the first blank space and paste into a new file. It worked. If you copy and paste whole dumped content you would see the visible unicode. Delete it.

When I dumped the file, I saw an unexpected blank space at the very front of the first line. I thought it was the culprit. I also noticed that** 'cat foo.h > bar.h' didn't get rid of the invisible character**.  Copy and Paste!
