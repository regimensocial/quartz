---
title: Citrahold's Development Now
date: 2024-01-08
tags:
  - programming
  - shorter
---
Citrahold is the name for the service/software I've been developing for the PC, 3DS, (and as a server). It allows you to move saves back and forth between the Nintendo 3DS and the PC for if you're using an emulator. Much greater explanation [[2023#Citrahold|here]].

I've been waiting to get it approved on Universal Updater before I do any major promotion, yet I've still gained a few users who've come and gone.

I need to keep development going though as it's something to keep me occupied and the ball is already rolling. No need to have it stop.

For now I have a few ideas for things I need to implement, I think once they're implemented, I'll just promote it anyway, regardless of whether it's approved on Universal Updater.

## The Small Ideas
Remember none of these are implemented at the time of writing.

### Direct Download
At the moment, Citrahold 3DS downloads everything to a new folder named "Citrahold-Download". This is to allow you to easily import it using Checkpoint.

It might be a good idea to allow people to download it directly to a folder, rather than create a new folder each time. This is for weird cases where someone is somehow running Citrahold 3DS on a platform where unencrypted saves are wanted.

I'm mainly talking about Citra Android. Citra Android works terribly for me, but it might work better for others. Another idea would be to actually just make an Android client, but that is a lot more work and I'm not sure if I want to learn Android development at this time... I have avoided app development for such a long time, feels like I'd want a more interesting project to initiate the whole app development journey.

### Accountless/Local Transfer
This one probably isn't that small an idea, but it might only take an evening to get a semi-working version.

#### Current System
Citrahold Server is essentially how Citrahold works. If you break it down, Citrahold is just a 3DS and PC client who send and receive files stored on a server (Citrahold Server). Due to the way that this works, you need an account.

The current system works fine, but some people feel a bit funny about signing up for bizarre services (which Citrahold definitely falls into). Websites even at the corporate scale can be terrible at storing user data responsibly. I don't store any unnecessary user data, and all passwords are hashed by bcrypt, but still it's reasonable to feel weird about your data being on a random server. Especially if that server is unfortunately provided by OVH (thinking of switching soon).

Everything is open-source though, and when I do promote this, I'm going to write some READMEs for each repo, which will give you information on how to run your own instance of Citrahold Server. This gives you more control and also takes some pressure off of me to host.

The current system also allows you to keep a save in the cloud safely. If you connect to McDonald's WiFi with your 3DS and upload a save, and then accidentally leave your 3DS at said McDonalds, when you get home, you can download it. 

#### Proposed New System
The accountless, or more, local transfer would be eliminating Citrahold Server. I say this but it's more like transferring Citrahold Server to one of the clients (3DS or PC, probably 3DS).

This way, instead of logging in on both the clients, you'd have to point one of the clients at the other and then treat one like a server. I think this is usually done by having one of them display its private IP address, and then manually typing it into the other. It should be possible to have the clients auto-detect each other (`3dslink`, used during development, manages to do this).

This would be hugely beneficial. The only caveats to the user are that they need to have both the 3DS and PC online and on the same network, and also the user must have both the PC and 3DS on them at the time. So you'd be out of luck if you leave the 3DS at McDonald's this time. Additionally, if the Citrahold Server instance I provide ever goes offline, the software isn't just useless bytes on your devices.

Writing all of this now has only just made me realise that this would be quite an endeavour; it would mean essentially rewriting the server in C++... The current one is written in JavaScript. This would be fun because it's generally advised not to use C++ for web backends, and it would be cool to have a reason to.

The issue would now be to figure out which end should host the server, the 3DS or the PC. Maybe both of them, for the hell of it. We'll see. 

#### Bottom Screen
At the moment the bottom screen of the 3DS client is just a console. It's currently useful because it tells you if downloads and uploads are successful. It was also an easy way for me to give more information to the user as the way I made the top screen restricted you to only making drop down menus essentially.

This idea is just to give an interface to the bottom screen. Make a prettier way to display information.

I'm not too concerned about adding touch controls, I quite like using the physical buttons on the 3DS, and adding touch controls would mean a complete UI overhaul which isn't really worth the time at this point.

This whole idea is the lowest priority for now.

Thanks for reading. As always, my email is at the bottom of the page. Please feel free to email me for literally any purpose.
