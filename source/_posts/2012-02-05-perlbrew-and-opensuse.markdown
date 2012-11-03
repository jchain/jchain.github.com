---
comments: true
date: 2012-02-05 06:08:45
layout: post
slug: perlbrew-and-opensuse
title: Perlbrew and openSUSE
wordpress_id: 339
categories:
- Linux
- Perl
tags:
- Perl
---

I have heard about how great [perlbrew](http://perlbrew.pl/) is from time to time on the web but I have never had a chance to play with it until today. After my openSUSE was upgraded from 11.x to 12.x and system-wide Perl was upgraded from 5.12 to 5.14, my local Perl modules was broken. I think it is a good idea to have access to multiple Perl distributions and a good management among them. Soon I realized that it was time to give perlbrew a try. I tried to install a locally built Perl-5.14.2 by the command

[sourcecode language="bash"]

perlbrew install perl-5.14.2

[/sourcecode]

But quickly it failed with the exactly the same error like [this](http://www.gossamer-threads.com/lists/perl/porters/234587). It was about something wrong with ODBM_File. And this problem seems specific to openSUSE. As the post link said, the solution is

[sourcecode language="bash"]

perlbrew install perl-5.14.2 -D noextension=ODBM_File

[/sourcecode]

This made a good build of perl-5.14.2. I further installed cpanm with perlbrew and replaced the system-wide cpanm. I've found it a better way to install CPAN modules since by doing so cpanm will install modules for difference versions of Perl in separate locations. For example, modules for Perl-5.12 won't conflict with Perl-5.14. This is just what I want.

Happy perlbrewing...
