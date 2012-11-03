---
comments: true
date: 2010-12-06 02:51:14
layout: post
slug: using-openmp-with-cmake
title: Using OpenMP with CMake
wordpress_id: 39
tags:
- C/C++
- CMake
- OpenMP
---

Add the following lines into your CMakeLists.txt
# Even though -fopenmp won't appear in the GUI options, it does take effect
SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -fopenmp")
SET(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -fopenmp")


