---
comments: true
layout: post
title: 'Watch Netflix in Linux'
date: 2013-11-29 13:09:00
comments: true
categories:
- Linux
tags:
- Linux, Wine
---

I had watched TV shows on [Hulu][2] for a simple reason that it's Flash-based so I could watch it in
Linux. One thing I did't like about Hulu is its high-frequency of ads. [Netflix][3] has fewer ads
but it builds its business on Silverlight plugin, which is generally exclusive for Windows and Mac
OS. I've never imagined that I could be able to watch movies in Linux until I found [Pipelight][1].

Pipelight is a very smart project that makes use of [Wine][4] to make Silverlight work in Linux web
browser. The website of Pipelight has provides a very complete documentation on the installation for
various Linux distributions. For me the installation for Fedora 19 was a breezy. Of course, you also
need some Firefox [plugin][5] to make Netflix believe you are using Windows Firefox. When you first
load Pipelight, Wine will automatically configure everything including downloading Silverlight.
I like this plugin so much. I don't think I will upgrade to Fedora 20 until Pipelight for that
version is available.

Only one thing I found worth mentioning this time is the update. If your Linux distribution updates
the version of Wine and your Pipelight doesn't work, my solution is to completely remove Wine and
Pipelight and then reinstall them.

You can how Netflix looks like in my Linux Firefox: ![alt][6]

[1]: http://fds-team.de/cms/articles/2013-08/pipelight-using-silverlight-in-linux-browsers.html
[2]: http://www.hulu.com
[3]: http://www.netflix.com
[4]: http://www.winehq.org
[5]: https://addons.mozilla.org/en-US/firefox/addon/user-agent-overrider/
[6]: https://db.tt/T0rNtnou
