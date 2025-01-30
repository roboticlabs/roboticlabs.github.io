---
layout: post
title: Install ROS2 Jazzy
date: 2025-01-01 10:11:00-0400
description: How to install ROS2 Jazzy step by step
tags: ROS toc sidebar
categories: posts
giscus_comments: true
related_posts: true
toc:
  sidebar: right
---

# Install ROS 2 Jazzy

In this tutorial, we will install ROS 2 Jazzy, Gazebo Harmonic and some useful packages.&#x20;

You will need a computer or virtual machine running Ubuntu 24.04, and you can follow the following guide to create a virtual machine from scratch:


## Introduction

ROS2 Jazzy Jalisco is the latest Long-term support version in 2025 that works comatible with Gazebo Harmonic:


For Gazebo simulator, there might be confusing about its version, and let's make it clear:

1. Basically, the "old" versions of _gazebo_ is called _classic_ like _Gazebo 11 (Gazebo+VersionNo.)_
2. There used to be a new Gazebo version called Ignition to replace the classic.
3. For some reason, Ignition is renamed to Gazebo again, and use _Gazebo+VersionName_ for the new generations of Gazebo simulator.
4. Although the new Gazebo has a different user interface with the classic, most of fundamental designs are same or similar, so it is not difficult to move to the new version. While there are lots of differences like the plugins, we will cover this in future tutorials.

For Gazebo Harmonic installation, there are two ways:

1. Install and run Gazebo Harmonic independently from ROS2.
2. Install and run Gazebo Harmonic with ROS2. For ROS developers, I recommend this way.

## Install ROS2 Jazzy

### Installation procedure


### Set Up the Environment Variables

After installation, you need to set up the important environment variables, which tell your computer how to find and use ROS 2 commands and packages. Open a terminal and type:

```
echo "source /opt/ros/jazzy/setup.bash" >> ~/.bashrc
```

