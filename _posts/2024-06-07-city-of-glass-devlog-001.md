---
layout: post
title: 'City of Glass Devlog #001'
date: '2024-06-08'
category: gamedev
---

This is the first of what I expect to be many devlogs for City of
Glass, the game I'm working on as a solo indie dev.

City of Glass is a game about a girl searching for her missing father,
an alchemist and scholar. She follows him to Thera, the titular City
of Glass, home of a university and what seems to be anachronistically
advanced works of architecture and medicine. During her quest, she
joins the Resistance, patriots of the Republic of Venice plotting
against the Ottoman Empire the city has since become a tributary
of. There's adventure, mystery, intrigue, and horror. It's inspired by
story-driven point-and-click adventures like _Gabriel Knight_, but
also games that play with themes of helplessness and vulnerability,
like the softcore-pornographic Neverwinter Nights module _A Dance With
Rogues_. The protagonist is a seventeen year old village girl alone in
a big city for the first time, developing her own sense of self. It's
up to the player to direct and guide it.

I've been quietly working on this for the last six months; I have
puzzle design graphs, design docs, and notebooks with sketches of
environments and scenes through the game. I've settled on a tech
stack, using the adventure game engine
[Popochiu](https://carenalga.itch.io/popochiu) designed for the latest
version of [Godot](https://godotengine.org/). Popochiu's version 2 is
still in beta, but it's been stable enough for me to put together a
minimum playable prototype of the first act of the game.

Most of the iteration on the narrative design, however, I'm doing in
Inform7 and in plain text. This allows me to add characters and rooms
on the fly, without a need for even placeholder art, and see what
makes sense. The interface is very different-- parser-based rather
than menu-driven-- and I'm debating using a different IF-authoring
tool, such as [Twine](https://twinery.org/) and
[Ink](https://www.inklestudios.com/ink/), to hone in on the
dialogue. For now, though, the focus is on the world.

The game starts in the village, which is smaller and easier to
model. The move to the city is where it gets tricky. I want to convey
a sense of vastness and overwhelm, while taking into account my
limited resources as a solo indie dev. Right now the assumption is
that the city will have a map and points of interest the player can
visit and revisit as they unlock through solving the mystery. This is
the approach most modern games set in urban locations take; but it
prevents the player from exploring the neighborhoods. I'm still
playing with where to go for this.

More as I know it.

