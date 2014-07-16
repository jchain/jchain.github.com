---
comments: true
date: 2012-09-14 16:29:58
layout: post
slug: use-perl-like-sed
title: Use Perl like sed
wordpress_id: 357
categories:
- Perl
tags:
- Perl
---

Recently I wanted to use Perl and Bash to deal with a large number of files. I ended up needing
in-line string substitution to create new shell commands. I vaguely had an idea that I should use
'sed' to do the text transform but by any chance I would like to use Perl. I rarely use Perl as
one-liner. It turned out that this is the correct way to do so

    find . -name "*.java" -print | perl -ne 's/java/java.old/g && print'
