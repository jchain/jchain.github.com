---
comments: true
date: 2011-11-09 22:00:24
layout: post
slug: midnight-commanders-new-user-data-directory
title: Midnight commander's new user data directory
wordpress_id: 284
categories:
- Linux
tags:
- Linux
- tips
---

It seems that the user-specific data/config directory of midnight commander 4.8.x is under
$HOME/.local/share/mc and $HOME/.config/mc. However the previous version(4.7.x) is looking for
$HOME/.mc. You can verify that by typing

    mc -F

Personally I don't like this change since I prefer to a single directory for the convenience of
storage and backup of my config files. Your skin setting probably take no effect after upgrading to
4.8.x. Place your skin files to `$HOME/.local/share/mc/skins` and modify `$HOME/.config/mc/ini`
