---
comments: true
date: 2011-03-12 06:16:18
layout: post
slug: update-your-display-environment-variable-for-nomachine-and-screen-user
title: Update your DISPLAY environment variable for Nomachine and Screen user
wordpress_id: 155
tags:
- Bash
- Linux
- Screen
- tips
---

If you are Nomachine and GNU Screen user, have you been annoyed by the problem that you can't start GUI program in a screen session? The reason to the problem is that the environment variable DISPLAY is not properly set when you attach a screen session. There are two posts talking about how to update environment variables such as SSH and DISPLAY  to make the life much easier.

[http://samrowe.com/wordpress/ssh-agent-and-gnu-screen](http://samrowe.com/wordpress/ssh-agent-and-gnu-screen/)/

[http://alan.lamielle.net/2009/03/09/environment-variables-and-gnu-screen ](http://alan.lamielle.net/2009/03/09/environment-variables-and-gnu-screen)
