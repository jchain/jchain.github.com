---
comments: true
date: 2010-12-08 22:26:07
layout: post
slug: convert-ogv-to-flv-in-linux
title: Convert ogv to flv in Linux
wordpress_id: 50
tags:
- Linux
- tips
---

I use recordMyDesktop to grab the screen movie but its default format is in ogv. If you want to convert to Flash format locally you can use the following command. Feel free to add it in your bashrc. If I recall correctly, this method can produce the best conversion in Linux platform. Correct me if I'm wrong. Also I forgot the source the following tip. If you know it, let me know.

`
# Convert ogv to flv.
# Usage: ogv2flv input.ogv -o output.flv
# add -audiofile yoursound.wav if you need to replace the soundtrack alias ogv2flv='mencoder -of lavf -oac mp3lame -lameopts abr:br=56 -srate 22050 -ovc lavc -lavcopts vcodec=flv:vbitrate=250:mbd=2:mv0:trell:v4mv:cbp:last_pred=3 -vf scale=640:480'
`
