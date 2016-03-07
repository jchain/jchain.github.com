---
comments: true
layout: post
title: 'Fix the loading dll issue of Octave Cygwin'
date: 2014-08-04 13:49:00
comments: true
categories:
- Octave
tags:
- Octave, Cygwin
---

Have you run into this loading problem when you start Octave in Cygwin recently? If yes, you are not
alone.

    [zandy@cygwin] ~ $ octave
    /usr/bin/octave-cli-3.8.1.exe: error while loading shared libraries: ?: cannot open shared
    object file: No such file or directory

Diagnose:
---------

    [zandy@cygwin] ~ $ cygcheck /usr/bin/octave-cli-3.8.1.exe
    C:\cygwin\bin\octave-cli-3.8.1.exe
    cygcheck: track_down: could not find cygblas-0.dll
    cygcheck: track_down: could not find cygblas-0.dll
    cygcheck: track_down: could not find cyglapack-0.dll
    cygcheck: track_down: could not find cyglapack-0.dll
    cygcheck: track_down: could not find cygblas-0.dll
    cygcheck: track_down: could not find cyglapack-0.dll
    cygcheck: track_down: could not find cygblas-0.dll
    cygcheck: track_down: could not find cyglapack-0.dll

It looks like Octave cannot find the shared libraries of `blas` and `lapack` but they actually have
been installed.

Solution:
---------

The loading issue is cause by the fact that `cygblas-0.dll` and `cyglapack-0.dll` were accidentally
installed into `/usr/lib/lapack`. According to the [Cygwin documentation][1], Cygwin looks for DLL's
by searching the directories defined in the environment variable `PATH`. The default `PATH` doesn't
include `/usr/lib/lapack`. Therefore, the solution is either

    cp /usr/lib/lapack/*.dll /bin

or

    export $PATH=/usr/lib/lapack:$PATH


[1]: https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/4/html/Using_ld_the_GNU_Linker/win32.html


<!-- vim: set fdm=expr ft=pandoc sw=4 ts=4 tw=100 : -->
