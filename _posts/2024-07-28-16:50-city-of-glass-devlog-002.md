---
layout: post
title: 'City of Glass Devlog #002'
date: '2024-07-28'
permalink: /2024/07/28/city-of-glass-devlog-002.html
categories: 
- gamedev
- city-of-glass
---

I'm back from Narrascope, and continuing to work on City of
Glass. I've had a couple friends playtest the opening act in both the
Inform prototype and the actual game engine (with scratch graphics).

Learning how to do placeholder graphics properly has been a process in
itself. I've tried scanned thumbnail pencil sketches, cartoonish
paintings, and most recently, wireframes. While the first two have
been useful for conceptualizing the game space, the pixel art
wireframes have been by far the easiest to iterate on. I can add
geometry, change the layout, and resize things quickly and
effortlessly, without worrying about making things pretty. Paths,
doors, and important hotspots are blocked out, but only rendered in
geometric shapes. I was worried that this would be a distraction to
playtesters, but it hasn't been an issue.

![Cutscene with placeholder graphics at the current level of quality.](/assets/images/posts/city-of-glass-devlog-002.png)

The dialogue user interface, however, has been.

Parser games do not lend themselves well to dialogue. Conversations in
them tend to either be pre-scripted, or involve a silent protagonist
asking and telling things. Most point-and-click adventures, however,
tend to feature a protagonist with a strong personality, who can ask
questions but does so in their own words, in an entertaining
fashion. In City of Glass I want the player to be able to roleplay and
define the protagonist's personality, and not put words into their
mouth. 

This means I'm going to need to flesh out the conversation system a
bit to display the narrative. I've recently become fond of
[Dialogic](https://github.com/dialogic-godot/dialogic) for Godot,
which drills down to [Ink](https://www.inklestudios.com/ink/)-like
plain text for representing branching dialogue flow. 


