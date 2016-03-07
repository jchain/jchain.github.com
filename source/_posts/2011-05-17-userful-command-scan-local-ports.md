---
comments: true
date: 2011-05-17 06:03:15
layout: post
slug: userful-command-scan-local-ports
title: 'Userful command: scan local ports '
wordpress_id: 172
categories:
- Linux
---

    netstat -antuwp | egrep "(^[^t])|(^tcp.*LISTEN)"
