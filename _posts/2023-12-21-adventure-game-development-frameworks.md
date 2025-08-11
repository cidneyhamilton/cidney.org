---
layout: post
title: 'Adventure Game Development Frameworks'
date: '2023-12-21 23:14:35 +0100'
category: gamedev
---
People often ask what tool to use to get started making adventure games. These are the five I've worked with in the past.

## [Adventure Game Studio](https://www.adventuregamestudio.co.uk/)

Adventure Game Studio, or AGS, has been around for *forever*. Since 1997. It's Windows only, built off of .NET, and does NOT run in wine, which is the main reason I haven't spent much time with it. I'm friends with AGS developers and have nothing but good thing to say about the community. If you have minimal programming experience, primarily use Windows, and want to get started making your own adventure games, it's probably the place to start. That said, I would not use it for my own projects because it requires Windows.

## [Adventure Creator](https://www.adventurecreator.org/)

Unlike AGS, I've used and shipped several games with Adventure Creator. It's an Asset Store package for Unity3D and costs about $80, but includes software that's well-maintained with a very active community. Chris Burton is awesome and very responsive to questions and feedback on the forums. It supports 2D and 3D games natively.

The main thing that can be frustrating is that it's geared at nonprogrammers-- so scripting is somewhat cumbersome and based around visual tools. This can be a bit time consuming. The main drawback for me is that it's part of Unity's proprietary ecosystem (so compatibility with third-party tools, like ink for writing, can be a pain when Unity or AC upgrades).

## [PowerQuest](https://powerquest.powerhoof.com/)

PowerQuest is another adventure game framework for Unity. It's aimed at making pixel art games with sprite animation-- something that Unity's default animation tools make rather cumbersome. The scripting language is text-based and much more like AGS.

Probably best if you're coming from AGS and want to use Unity.

## [Escoria](http://escoria-framework.org/)

If you DON'T want to use Unity, and want to use exclusively free software to make your game, people will point out Godot. Godot is lightweight and a breeze to use compared to Unity. The editor itself is designed in Godot; compared to Unity UI the tools for making user interfaces are great to work with.

Escoria has been around since [2016](https://godotengine.org/article/our-point-click-framework-finally-out/). Like Godot, it's free software under the MIT license. However, since it's being maintained by people with very limited time, it's struggled to keep up with Godot itself. Currently it's only in alpha and only available for version 3 of Godot. It also seems aimed at high-res graphics, not pixel art.

## [Popochiu](https://carenalga.itch.io/popochiu)

Popochiu is a very new framework for Godot, inspired by PowerQuest and AGS. The dev team and video tutorials are in Spanish with English subtitles, but the dev team is very active and responsive. I've switched from Escoria to Popochiu for my solo indie game and am loving it so far. It supports high-res graphics and low-res pixel art.

The biggest downside is that because it's so new there aren't many integrations with other tools (such as Ink). There's some integration with Aseprite for sprite-based workflows. This is all very fixable, though.

## Others

This is not an exhaustive list. I've never used [Visionaire](https://www.visionaire-studio.net/) or Unreal Engine's [point-and-click framework](https://www.unrealengine.com/marketplace/en-US/product/point-and-click-adventure-toolkit), so can't compare them.
