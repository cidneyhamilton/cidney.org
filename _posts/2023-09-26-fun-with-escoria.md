--- 
layout: post
title: Fun with Escoria
date: 2023-09-26
---

I've been using [Godot](http://godotengine.org), a free and open source game general-purpose game engine, on and off for years, ever since a friend recommended it as an alternative to [Unity](https://unity.com/). I've been doing contract work with Unity for a while, but for my own games, I'd prefer to use FOSS tools where possible. However, most of the non-contract gamedev I've done has been for game jams, which are strictly timed and make experimenting hard. I ported a Ludum Dare entry to Godot a few years ago and discovered that this was more work than anticipated.

For adventure games on a timeline or budget, it's almost always better to start with a framework. There's allegedly been a framework, [Escoria](https://docs.escoria-framework.org/en/devel/), for developing point-and-click-adventures in Godot for a while, but it's never been in a stable state, and I've never had time to investigate too deeply.

This month, I took some time to investigate more deeply, going through the tutorials, talking to the devs on Discord, and submitting pull requests. There's an Asset Library version of Escoria, but it's woefully out of date; the project is in the process of becoming more modular with separate libraries for UI, dialog management, and the core framework. Best practice for now is to start with the [demo game](https://github.com/godot-escoria/escoria-demo-game), copy over resources into a new project, and begin.

I've been able to get the first six rooms of the game I'm working on prototyped, and Escoria integrated with [Ink](https://github.com/inkle/ink), my preferred language for branching dialogue. Ink has been supported in Godot for a while, though the GDScript plugin warns that it's not performant for commerical games. I can always switch to C# and Mono when I have to.

Some quirks of the framework:

-- very few primitives. no NPCs, hotspots, etc. All of these derive from the same base class, ESCItem. NPCs are not distinguished from static items.
-- by default, the player moves to the center of a hotspot or defined waypoint (child ESCLocation) when interacting. This is in contrast to Adventure Creator, where defining the behavior when interacting with a hotspot (turn to face? walk to waypoint? what waypoint?) is specified in the hotspot properties. Instead there's a [TK](https://docs.escoria-framework.org/en/devel/scripting/z_esc_reference.html#event-flags), telekinesis, flag in the Escoria scripts to prevent the default walking over behavior.
-- no local variables; everything is a global. this may not scale well for large games with doors and containers that can be opened or closed.

All in all, very pre-alpha, but very promising. I wouldn't want to use it for a commercial project just yet, but want to keep an eye on it for the future.
