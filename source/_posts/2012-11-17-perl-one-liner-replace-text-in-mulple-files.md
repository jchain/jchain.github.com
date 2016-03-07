---
layout: post
title: 'Perl one liner: replace text in mulple files'
date: 2012-11-17 02:10
comments: true
categories: 
- Perl
---

Today I got some time to improve my tech blog with [Octopress][1]. I found that I couldn't use the
different letter cases as the same category name. Otherwise the category page wouldn't show correct
number of links to the posts under that category. For example, I had to change all `git` to `Git` in
the meta info of every posts. Here was what I used to get this job done.

    ack "\- git" *.markdown -l | xargs perl -p -i -e 's/- git/- Git/g'

A little explanation:

    -l: ask ack to only show the filename with matched search pattern. You can try first without -l
        option to make sure you find the correct files. And then run with -l option to make the output
        suitable for xargs
    -p: read and loop from files instead of STDIN
    -i: in-place edit
    -e: run the command. Here we do the search and replace operations.

[1]: http://octopress.org
