--- 
layout: post
title: Developing for Quest 2 with Linux and Unity in 2023
date: 2023-04-14
permalink: /2023/04/14/developing-on-quest-2-with-linux.html
category: gamedev
---

I've been helping out with the [Transit Costs
Project](https://marroninstitute.nyu.edu/projects/transit-costs-project)
at New York University lately. I'm partnering with a game artist to
simulate a proposed redesign of Penn Station. Earlier this week, I took out my old VR headset to get a VR version of this.

I began doing VR rather unexpectedly in 2021 for [another game](https://www.colossalcave3d.com/). The problem is that Facebook/Meta dropped support for development on Mac and Linux a while ago; it's possible to develop by making and installing standalone Quest builds, but it's not as simple as just pressing play and testing things out in the headset, as in Windows. I wouldn't want to do this full-time, but for this project getting things working was pretty simple.

I've used [Devin Willis's](https://devinwillis.com/2019/11/29/oculus-quest-development-with-linux-and-unity3d/) guide as a starting point, but this hasn't been updated since 2019. In 2023, things are a bit different.

## Installing Android Dependencies

I used Unity 2021.3.2, with Android Build Support and all related packages. Unity installed OpenJDK, OpenNDK, and OpenSDK, which saved time installing them by hand.

![Screenshot of Unity Installation](/assets/images/unity-screenshot.png)

# Installing Gradle

Gradle was a different story. My first build failed, and Gradle needed to be installed by hand. I used [SDKMAN!](https://sdkman.io/) to install the latest Gradle, then updated Unity's preferences to point to the new Gradle installation.

```curl -s "https://get.sdkman.io" | bash```

```sdk install gradle 8.1```

This needs to be assigned in Unity's Preferences.

![Screenshot of Unity Preferences](/assets/images/unity-preferences-screenshot.png)

From there it was straightforward to connect the device and do a test build.
