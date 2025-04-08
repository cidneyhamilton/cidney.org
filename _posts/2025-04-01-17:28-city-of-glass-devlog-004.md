---
layout: post
title: 'City of Glass Devlog #004'
date: '2025-04-07'
---
Happy April! I'm back in New York and the days are getting sunnier and warmer. It's April, the month that City of Glass canonically begins.

I'm still the sole developer on the project, and have been adding placeholder art and music. I expect to hire contractors to help with both of these things as the game progresses, but I want to have everything playable with placeholder assets first before figuring out a budget for that. In the meantime, it's been good motivation to get back to the piano and spend a significant time with my sketchbook. Making music helps relax and calm me-- and giving myself permission to improve and compose is helpful. Similarly, so does drawing and painting. The last point-and-click adventure game I worked on relied extensively on rotoscoping for the pixel art assets. I'm not committed to an art style yet, but I've gotten more confident in my sense of proportion and the ability to render the human figure. I've been following Alex Honeycutt's [curriculum for the solo artist](https://www.reddit.com/r/learnart/comments/dapk62/from_the_guy_who_made_the_most_comprehensive_list/) from 2019 and have been shocked by how much my ability to render the human head and figure has improved. Enough to appreciate what goes into the process.

Environments are proving to be the challenging thing. Some adventure
games are fairly static, but since this is an RPG, time progression is
important. Every outdoor environment has a day, night, and sunset
version, and NPCs follow different schedules and are available at
different times of day. The player can progress time if they can find
a safe place to rest, but finding food and shelter in the village is
not trivial. While the protagonist has inherited her father's
apartment in the city, she starts the game homeless and penniless
until she can find a way to get to the city. Once there, food is
scarcer and more expensive, and she'll need employment. But many shops
and businesses close up early; and she'll soon run into conflict with
her obligations to the Resistance and her obligations to her employer.

Animations are getting a significant amount of work. The main character has four different outfits, all of which require a separate set of animations. These are currently hand-drawn, without the use of bones. I'm currently making use of Aseprite import scripts for Godot to easily import character and environment art into the game and iterate on it when designing rooms, but the more animations that get added, the trickier this becomes.

With the content for the game in, I'm going to dive into the core game system-- the dialogue interface. Since my background is heavily in interactive fiction and this game is heavily character-driven, most of the heavy lifting is there. [Dialogue Jam](https://itch.io/jam/dialogue-jam-25) is taking place next month, and I have a short game I want to do for it, but with all of the traveling I'm doing won't have time for a break until the end.

For those of you who have been following my progress and asking about it-- thank you! More updates will come soon.
