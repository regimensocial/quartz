---
title: Palworld Server Helper
date: 2024-02-03
tags:
  - programming
  - very-short
---

This is going to be quite a short one (for me at least).

## Palworld!

Palworld is a game that likely needs no introduction. But if you've not heard of it, it's a survival adventure game with stolen Pokemon slapped on. I don't want to add too much more of an opinion because I really do enjoy the game, but I must also agree that they're definitely on thin legal ice (if it's not already in the water)... It'll be interesting to see if Nintendo do retaliate.

It's an "early access" game and it really REALLY deserves that title.  

Regardless, if you're playing the Steam copy of it, you can make a dedicated server for it.

## Getting a server

I'm playing it with my friend, but we both have different schedules. We can't often play together but still want to play on the same world together. I've ran game servers many times, notably Minecraft.

We scrambled some change together before payday and are currently renting a server out in Nuremberg. Shout out to Hetzner for good servers. I use OVH for everything else just because it would be too much hassle to move everything over at this point, but if you're looking for a good provider, I'd probably recommend Hetzner. The only thing I don't like about Hetzner is that you can only get servers in Germany or Finland, OVH is good for me since they do have datacentres in the UK.

## The Issue(s)

Anyway, the Palworld Dedicated Server is really poorly coded and apparently doesn't even save half the time. Even worse, it has really bad memory leaks. From my observation, I don't think memory usage ever lowers naturally.

They'll likely fix these issues but playing on a server with issues like this *does* give me some anxiety. It's the kind of problem I can fix. Other people have also created solutions, but I wanted a solution which would work well enough with my ecosystem (Node.js).

## Development

I programmed it all on a weak Debian laptop from 2012 because I was away from home, it was able to run the server for testing (albeit, VSCode froze sometimes during the process).

Development went alright but it was the first time in a while where I'd had Node.js spawn child processes. 

The major setback was RCON, which is Valve's communication protocol for servers. The server doesn't run like a Minecraft server (or any intuitive server) where you can just use the console to write a command like "/Save" and have it save. You HAVE to use RCON to send commands to it. Not the biggest fan of this approach since it means having another port exposed in some capacity, and also it's unnecessary.

Finding libraries in Node which worked with RCON just was impossible. Everything I tried failed, so I just used ARRCON, a third party open source command line tool. The Node script just runs this tool to do whatever is needed.

## Features

I made a really horrible looking web panel for it. This could all be worked on, I just wanted something that would work well and let me rest easy.

By default, every 15 minutes, it saves the game. Every 6 hours, it restarts the server. Every 12 hours, it backs up the server. If there's ever a crash, it'll do its best to restart the server.

## Repository

You can see the code for it [here](https://github.com/regimensocial/PalworldServerHelper). I don't think it's my best work, but it's fairly clean and reliable. Also there's a proper guide on how to set it up which I was happy to make.

People are using it? It has over 100 clones at this point, which is definitely more than just me. It might just be automatic cloners, but this is far beyond my other repositories. I'm curious if people are actually using it, or if people just tried to set it up or had a peek. 

Situations like these make me wish GitHub had some kind of comment section, but it's not meant to be a social media platform. It's meant to be an ***AI driven programming platform***, obviously. 

I know it seems like I'm giving a lot of flak to the developers here, it is an "early access" title, but they are charging £24 for this experience. You'd expect things to be in slightly better condition.

Thanks for reading. As always, please email for any purpose (especially if you end up using it, just quite curious).