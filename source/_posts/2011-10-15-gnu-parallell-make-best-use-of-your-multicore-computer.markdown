---
comments: true
date: 2011-10-15 00:13:16
layout: post
slug: gnu-parallell-make-best-use-of-your-multicore-computer
title: GNU Parallell, make best use of your multicore computer
wordpress_id: 251
categories:
- Linux
tags:
- Linux
- tips
---

In my research work, I have to run many many times of the same program with different parameters.
I wrote bash files to make my life easier. But single process of bash is very slow considering
I have a decent computer with 24 cpu cores. My old way to make better use of multicore CPU was to
split my jobs into several separate bash files and run them simultaneously. You can imagine that it
is far from productive when editing these files. They contain overwhelmingly repeated text.

GNU [parallel](http://www.gnu.org/s/parallel) comes to rescue. I first ran into this post
[http://pebblesinthesand.wordpress.com/2008/05/22/a-srcipt-for-running-processes-in-parallel-in-bash/](http://pebblesinthesand.wordpress.com/2008/05/22/a-srcipt-for-running-processes-in-parallel-in-bash/).
But I quickly found GNU parallel was a better choice. Fully loaded with detailed documentation.
Plus, it was written in Perl. As you may know, I'm a Perl fan:-). Now my batch file has become like
this:

    seq 1 100 | parallel -j 20 single_run.sh {}

Voilà!
