---
comments: true
date: 2010-03-24 05:37:24
layout: post
slug: cmake-cannot-determine-link-language-for-target
title: '[CMake] Cannot determine link language for target?'
wordpress_id: 30
tags:
- C/C++
- CMake
---

For whatever reason add

    
    SET_TARGET_PROPERTIES(XYZ PROPERTIES LINKER_LANGUAGE C)
