---
layout: post
title: Install ROS2 Jazzy
date: 2025-01-01 10:11:00-0400
description: How to install ROS2 Jazzy step by step
tags: ROS toc sidebar
categories: sample-posts
giscus_comments: true
related_posts: true
toc:
  sidebar: right
---

# 1.1 Install ROS 2 Jazzy

In this tutorial, we will install ROS 2 Jazzy, Gazebo Harmonic and some useful packages.&#x20;

You will need a computer or virtual machine running Ubuntu 24.04, and you can follow the following guide to create a virtual machine from scratch:

{% embed url="https://youtu.be/zcisXWGHcAg" %}

## Introduction

ROS2 Jazzy Jalisco is the latest Long-term support version in 2025 that works comatible with Gazebo Harmonic:

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption><p><a href="https://docs.ros.org/en/rolling/Releases.html">https://docs.ros.org/en/rolling/Releases.html</a></p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption><p><a href="https://gazebosim.org/docs/harmonic/ros_installation/">https://gazebosim.org/docs/harmonic/ros_installation/</a></p></figcaption></figure>

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

{% embed url="https://docs.ros.org/en/jazzy/Installation/Ubuntu-Install-Debs.html" %}

### Set Up the Environment Variables

After installation, you need to set up the important environment variables, which tell your computer how to find and use ROS 2 commands and packages. Open a terminal and type:

```
echo "source /opt/ros/jazzy/setup.bash" >> ~/.bashrc
```

This wil add the line **source /opt/ros/jazzy/setup.bash** to your **\~/.bashrc file**.&#x20;

Why do this? Each time you open a new terminal window, you are starting a **bash session**. The bash session needs to know what version of ROS 2 you are using. By adding this line,  you can use ROS 2 Jazzy commands and tools without having to manually run the setup.bash script every time.

To take effect, open a new terminal window, or run following cmd in the current terminal:

```
source ~/.bashrc
```

You can verify that line was added by typing:

```
sudo apt-get install gedit -y
gedit ~/.bashrc
```

### Check environment variables

If you ever have problems finding or using your ROS 2 packages, make sure that your environment is properly set up using the following command:

```
printenv | grep -i ROS
# Also, you can type:
echo $ROS_DISTRO
printenv ROS_DISTRO
lsb_release -a  #check Ubuntu
```

If the environment variables are not set correctly, return to the ROS 2 package installation section.&#x20;

Set up the system to manage ROS package dependencies.

```
sudo rosdep init
rosdep update
```

### Run ROS2 example - Turtlesim

Install turtlesim

```
sudo apt update
sudo apt install ros-jazzy-turtlesim
```

Start turtlesim

```
ros2 run turtlesim turtlesim_node
```

Open a new terminal and run control node

```
ros2 run turtlesim turtle_teleop_key
```

Install and run rqt tool

```
sudo apt update
sudo apt install '~nros-jazzy-rqt*'
rqt
```

## Install Gazebo Harmonic

To install Gazebo Harmonic binaries on Ubuntu 24.04 simply follow the steps [on this link](https://gazebosim.org/docs/harmonic/install_ubuntu/).

```
sudo apt-get install ros-${ROS_DISTRO}-ros-gz -y
```

### Test Gazebo Installation

If you want to run an example Gazebo simulation world now, you can type:

```
LIBGL_ALWAYS_SOFTWARE=1 QT_QPA_PLATFORM=xcb gz sim -v 4 shapes.sdf
```

<details>

<summary>The environment variables explanation</summary>

The environment variables “LIBGL\_ALWAYS\_SOFTWARE=1 QT\_QPA\_PLATFORM=xcb” help you avoid the following error which happens by default when you try to launch Gazebo from a fresh ROS 2 Jazzy installation:

_\[GUI] \[Err] \[Ogre2RenderEngine.cc:1301]  Unable to create the rendering window: OGRE EXCEPTION(3:RenderingAPIException): currentGLContext was specified with no current GL context in GLXWindow::create at ./.obj-x86\_64-linux-gnu/gz\_ogre\_next\_vendor-prefix/src/gz\_ogre\_next\_vendor/RenderSystems/GL3Plus/src/windowing/GLX/OgreGLXWindow.cpp (line 165)_

You can see the error, if you open a new terminal window and type:

```
gz sim -v 4 shapes.sdf
```

</details>

To make these environment variables permanent, open a terminal window and type:

```
echo 'export LIBGL_ALWAYS_SOFTWARE=1' >> ~/.bashrc
echo 'export QT_QPA_PLATFORM=xcb' >> ~/.bashrc
source ~/.bashrc
```

Now test your Gazebo installation again by typing the following command:

```
gz sim
```

Click on one simulation, and click Run. Close the simulation by typing CTRL + C in the terminal window.

## Install useful tools

Let’s install some other useful packages like pip (the Python package manager), NumPy (a scientific computing library for Python) etc.

```
sudo apt-get install python3-vcstool
sudo apt-get install python3 python3-pip -y
sudo apt-get install python3-numpy
```

Install terminator to show multiple terminal windows in a single window.

```
sudo apt-get install terminator -y
# to run it, type:
terminator
```

Right-click on the terminator screen, and click “Split Horizontally”.



## References:

[https://docs.ros.org/en/rolling/Releases.html](https://docs.ros.org/en/rolling/Releases.html)\
[https://docs.ros.org/en/jazzy/Installation.html#](https://docs.ros.org/en/jazzy/Installation.html)

[https://gazebosim.org/home](https://gazebosim.org/home)\
[https://gazebosim.org/docs/harmonic/ros\_installation/](https://gazebosim.org/docs/harmonic/ros_installation/)
