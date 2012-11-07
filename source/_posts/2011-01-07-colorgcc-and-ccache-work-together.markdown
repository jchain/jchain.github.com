---
comments: true
date: 2011-01-07 16:52:29
layout: post
slug: colorgcc-and-ccache-work-together
title: colorgcc and ccache work together
wordpress_id: 70
categories:
- GCC
tags:
- tips
---

The plain and lengthy output of g++ was a hurt to eye when your code contains a lot of template
programming. [colorgcc](http://schlueters.de/colorgcc.html) can make life easier. It can work well
with [ccache](http://ccache.samba.org/) but needs a bit trick to connect them together. I would like
to recommend the solution at

[http://stackoverflow.com/questions/1995415/g-colorgcc-and-ccache](http://stackoverflow.com/questions/1995415/g-colorgcc-and-ccache)

I copy the main part right here:


> 

> 
> ## The Short Answer
> 
> 
Without patching `colorgcc.pl` itself, the easiest way to fix this is to write yourself a simple wrapper script for each command, calling `ccache` with the appropriate arguments for that command, and passing along the arguments the script received (effectively [currying](http://en.wikipedia.org/wiki/Currying) the call to `ccache`.)

E.g., for **gcc**:

> 
> 
	
>   * **/usr/local/bin/ccache-gcc.sh:**

>     
>     <code>#!/bin/bash
>     ccache /usr/bin/gcc "$@"
>     </code>
> 
> 

> 
	
>   * **~/.colorgcc:**

>     
>     <code>gcc: /usr/local/bin/ccache-gcc.sh
>     </code>
> 
> 

> 

and for **g++**:

> 
> 
	
>   * **/usr/local/bin/ccache-g++.sh:**

>     
>     <code>#!/bin/bash
>     ccache /usr/bin/g++ "$@"
>     </code>
> 
> 

> 
	
>   * **~/.colorgcc:**

>     
>     <code>gcc: /usr/local/bin/ccache-g++.sh
>     </code>
> 
> 

> 

There are ways to clean this up so that you only use a single script,  with symlinks for each variant, but those are beyond the scope of this  answer, and I leave them to you as an excercise :-)
