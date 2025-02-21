---
layout: post
title: 'City of Glass Devlog #003'
date: '2025-02-21-13:53:00 +0200'
tags: devlog gamedev city-of-glass
---

This is the third devlog for my in-progress adventure/RPG, City of
Glass. The first two can be read
[here]({{site.url}}/2024/06/08/city-of-glass-devlog-001) and
[here]({{site.url}}/2024/07/28/16-50-city-of-glass-devlog-002.html)

I'm continuing to work quietly on City of Glass. I've released about a build per month and have drafted severely devlogs-- however, anxiety about the game itself seems to be the main challenge! I've spent many years working on other people's games, and doing small games for gamejams where I haven't had time to overthink it. Carrying out a project, from design to prototyping to executing a polished project, is a different challenge, and I often wonder if I'm not up for it.

Right now, I'm beginning to refine the art for the beginning. I don't know yet if I'll have the budget to hire an artist, so I'm doing everything myself. This means a great deal of my time is going into reviewing how to draw the people, animals, and environments that appear in my game. Placeholder art for characters and backgrounds are being refined. 

I'm trying not to spend too much time on any one art asset, since everything at this point is not final. But it's helping me figure out which parts are hards and which aren't. Coming up with a painterly sketch of a dreamy outdoor environment was easy-- designing a cluttered attic to appear believable has not been, and I've taken far longer on some backgrounds than others.

![Outdoor environment](/assets/images/posts/city-of-glass-devlog-003-1.png) 

![Interior](/assets/images/posts/city-of-glass-devlog-003-2.png)

On the programming end, I've settled on
[Ink](https://github.com/inkle/ink/) for scripting and
[Popochiu](https://github.com/carenalgas/popochiu) as a base game
engine. Popochiu's evolved rapidly during the time I've been
experimenting with it, and I'm continuing to develop my Ink Popochiu bridge. Much of my time is spent dealing with quirks of the engine. I often wonder how AGS would handle these edge cases, but not to the point of wanting to spin up a Windows partition and experiment.

Because City of Glass is an adventure/RPG, there are a number of core systems that aren't handled by the engine. I've added a character sheet, a day-night cycle, and the ability to swap out equipment in a paper doll interface. This vastly increase the number of animations I need, but it's worth it for the kind of game I'm making.
