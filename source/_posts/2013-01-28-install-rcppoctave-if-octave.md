---
layout: post
title: 'Install RcppOctave if Octave is in user-defined directory'
date: 2013-01-28 23:43
comments: true
categories: 
- R
- Octave
---

Even though I have been very busy these days I think I should try to get at least one post published
per month. My recent job involved a lot of data analysis and statistical computing. I pushed myself
to get familiar with [R][1] because some packages from R are indispensable for my work. Meanwhile
I also wanted to reuse my existing [Octave][2] code. Luckily I get the best of both worlds by using
[RcppOctave][3] which is a bridging package connecting the R and Octave sessions. 

I compiled the latest Octave on the server and installed in my home directory. When installing
`RcppOctave` in R by running

    install.packages('RcppOctave') 

I ran into an error message like this:

    ** preparing package for lazy loading
    Creating a generic function for ‘show’ from ‘methods’ in package ‘RcppOctave’
        (from the saved implicit definition)
    ** help
    Error : /tmp/Rtmp028JZY/R.INSTALL6dea26e533ee/RcppOctave/man/o_addpath.Rd:40: unable to load
    shared object '/home/zandy/lib64/R/library/RcppOctave/libs/RcppOctave.so':
    liboctinterp.so.1: cannot open shared object file: No such file or directory

    ERROR: installing Rd objects failed for package ‘RcppOctave’
    * removing ‘/home/zandy/lib64/R/library/RcppOctave’

The build phase seemed OK. Only did the install phase complain. I spent some time and figured out
a work-around is to specify the library path to your `liboctinterp.so`:

    export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$HOME/lib64/octave/3.6.3

I don't know much about the internal mechanism of `install.packages` otherwise I may be able to fix
the problem completely.

[1]: http://www.r-project.org
[2]: http://www.octave.org
[3]: http://cran.r-project.org/web/packages/RcppOctave/
