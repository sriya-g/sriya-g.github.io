+++
title = "The Homelab Experience"
date = 2026-01-17
+++
## Motivation
For a while now, I've been trying to get my data away from various cloud storage providers. I've been storing most of my files locally, but with only 300 GB allocated to my main Fedora install on my laptop, this isn't plausible in the long term.

I have an old PC lying around at home, and I've briefly entertained the idea of self hosting before. I usually dismiss it for various reasons. I don't currently have a domain name, I haven't looked much into software options, etc. 

About two weeks ago, I had some free time and decided to just start setting up [Tailscale](https://tailscale.com/) and [Nextcloud](https://nextcloud.com/).
## Setup
This was way easier than I expected. 
### Prerequisites
Surprisingly, the hardest part might have been setting up my PC. It used to be home to a Windows 11/Ubuntu dual boot, until I broke GRUB trying to install Linux Mint too -- the only survivor was the Windows install. The CPU didn't have official support for Windows 11 (it's a still-capable i7 that's just one generation too old) but I installed it through Windows Insider Preview a few years ago. Unfortunately, it refused to update properly, and I realized running W11 might not be feasible. It was time to switch back to Linux.

I chose Ubuntu again for software compatibility. It also seems to be a popular choice for running servers, so I rationalized i'd be able to find other people with my problem if a problem did arise. 

The only factor holding me back was that I didn't have a spare USB drive to use as installation media. I was very close to using an old Note 8 when I found a generic 8gb drive. To make future installs and livebooting easier for myself, I set up Ventoy on the drive.

Bizarrely, I was unable to access the BIOS with the HDMI plugged into my GPU, which was annoying. My "fix" was to just install Ubuntu with the HDMI plugged into the motherboard, then set up the GPU after the install finished.
### Actual setup
I set up Tailscale on my laptop, PC, and iPhone. Then, I followed [this guide](https://github.com/nextcloud/all-in-one/discussions/6817) to set up my Nextcloud on the PC.

That's it! I was able to access my Nextcloud on my laptop and phone.
### Sidenote: Syncthing
In the past, Syncthing was my main method of sharing files between devices. KOReader has a [Syncthing plugin](https://github.com/jasonchoimtt/koreader-syncthing), so I started using it for eBooks because my Kindle e-reader doesn't support USB file transfer while in KOReader. Later, I added my iPhone (with [Synctrain](https://github.com/pixelspark/sushitrain)) so that I could read the same books on my Kindle and phone. For the most part, this worked. Occasionally I ran into issues with annotation metadata file conflicts if I read the same book on KOReader on both my Kindle and laptop, but I usually read different books on different devices so it didn't happen often.

When I switched to Obsidian on iPhone, I wanted to sync my notes too, which is when I discovered a major limitation. I wasn't able to pick my vault location on iOS -- I had to have the vault inside the "Obsidian" folder on my iPhone. This meant that I wouldn't be able to directly use my vault folder in Nextcloud as the source for my notes. I was able to set Synctrain to sync my Obsidian vaults to this folder. 

When I set up Nextcloud, I backed up my eBooks and notes, but realized that I needed to maintain Syncthing for my Kindle ebooks. [It is possible](https://tailscale.com/blog/tailscale-jailbroken-kindle) to [set up Tailscale on a modded Kindle](https://blog.papermatch.me/html/Tailscale_on_Kindle), but it felt like overkill. I also needed some way of making sure my Obsidian vaults were mirrored directly to the Obsidian folder on my phone, and since Syncthing was working, I decided to keep it. I changed the Syncthing directory on my laptop for both folders to be in the directory I sync to Nextcloud.

This does mean my setup is more complex, since my note edits on iPhone don't automatically save to the cloud. I just need to remember to sync them (and my eBooks on my Kindle) with my laptop every once in a while.
## My Favorite Features
After I finished setting up the Nextcloud instance, I had a moment of looking at the tabs for all of the different apps and being overwhelmed at just how much was included.

Over the next few days, I explored the features and found my favorites.
### Calendar and Tasks
I've been looking for a good alternative to Google Calendar/Tasks for a while now. I used Proton Calendar for a year, but it doesn't have a Tasks equivalent right now. My replacement was a running list of To Dos on paper, which lacked several features I care about (sync, putting task due dates on the calendar.) Other options I explored online lacked these features, or they were proprietary, or had too many features I didn't want that would get in my way.

As it turns out, Nextcloud Calendar and Tasks are great replacements that do exactly what I want, and they sync with the native iOS Calendar and Reminders apps with CalDAV.
### [Music](https://github.com/nc-music/music)
I wanted an app to listen to my music collection, so I decided to try this. I liked the way the UI looked, and the Last.fm scrobbling support and Subsonic compatibility were promising. One of the main frustrations of trying to listen to music locally on my iPhone was that no app I checked had client-side scrobbling support for local music. Last.fm is the main way I aggregate my listening data from all the different places I listen to music ([Strawberry](https://www.strawberrymusicplayer.org/), my iPod, Bandcamp, YouTube.) VLC on iOS is amazing, it has a great UI and supports many different file types, but I eventually gave up on listening to local music files on my iPhone because I had no way to log it.

*sidenote: the awesome [Web Scrobbler](https://github.com/web-scrobbler/web-scrobbler) has a [Safari extension](https://apps.apple.com/us/app/web-scrobbler/id6449224218) that works on iOS. I only found out about this a few weeks ago, but I used it until I set up my homelab. If you find yourself mostly using the browser versions of the [many, many websites](https://webscrobbler.com/) supported by Web Scrobbler, give it a try!

I set up the Last.fm integration by adding my API key, downloaded an amazing Subsonic client on my iPhone ([Amperfy](https://github.com/BLeeEZ/amperfy)), configured Subsonic on Strawberry and Amperfy, and started streaming my music.

It worked perfectly! I was even able to scrobble the tracks I listened to on my iPhone. Amperfy also supports lyrics, which finally motivated me to use [LRCGET](https://github.com/tranxuanthang/lrcget) to get the .lrc (lyric) files for most of my library.

This is probably my favorite part of the entire homelab setup. I can't thank the people behind the Music app and Amperfy enough.
