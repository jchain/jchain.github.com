---
comments: true
date: 2010-11-24 04:40:44
layout: post
slug: install-lighttpd-as-a-service-in-cygwin
title: Install lighttpd as a service in Cygwin
wordpress_id: 6
categories:
- Cygwin
tags:
- Cygwin
- Web
---

    cygrunsrv --install lighttpd --path /usr/sbin/lighttpd
        --args "-D -f /etc/lighttpd/lighttpd.conf" --disp "CYGWIN lighttpd"

See more http://www.cygwin.com/ml/cygwin-apps/2004-09/msg00115.html
