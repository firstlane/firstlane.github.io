---
title: "Server Bot"
date: 2022-02-12T21:35:27-06:00
author: "firstlane"
---

## Intro
During Black Friday of 2021, I caved and decided to build a server PC. It was something I had been thinking about for a while, and I finally decided to pull the trigger after a friend was telling me about the NAS they were ordering. I started researching NAS/server builds and came across the [NAS Killer](https://www.serverbuilds.net/the-original-nas-killer-v10) and took heavy inspiration from this build when choosing components.

I finally received all the parts and got the computer put together after the New Year. The first things I got running on it where Valheim and Minecraft servers. The goal was to be able to leave the computer running 24/7 so that any of my friends could hop on if they felt like it.

There was one problem: the only port in my house that has active internet is in my bedroom, so I have the server in my room in order to hardwire it to the modem. I quickly found that the fans in the computer were too loud, so I had to keep remoting in each night to shut it off before going to bed. I got quite tired of this, and decided I needed a simpler solution.

I looked around a bit online to see what solutions there were for this problem. On a Reddit post (I forgot where), I found one commenter saying that he had made a custom solution that allowed him to send a message over an app and it would trigger a command on the server. I don't remember what app it was, possibly Discord or Slack; but after reading this, I decided it sounded like a lot of fun to write a Discord bot to send commands to the server.

## Implementation
Go has a good library for the Discord API called [discordgo](https://github.com/bwmarrin/discordgo) that I've used previously, so I decided to use it again here. I first setup a very simple bot that occasionally checks my public IP address using https://ipinfo.io/ip. If the IP address has changed since the last check, it sends me a notification on Discord with the new IP. This way, I can inform my friends so that they can continue breaking blocks in Minecraft and slaying Greydwarves.

With the code completed, I setup the bot inside a Docker container, following the steps in the [Go Docker tutorials](https://docs.docker.com/language/golang/build-images/). The code for this bot can be found [here](). <!--Link to a static .txt file with the code-->

With this initial bot setup, I proceeded to create a separate one to run on a Raspberry Pi Zero W. This bot would listen for messages from me on Discord and send an appropriate command to the computer. In hindsight, this bot could easily absorb the IP address checking functionality of the other bot and eliminate the need for two, but I did not think of this at the time since the IP address checker was the first need I identified. I will probably combine the two bots at some point (or I'll forget about it and have a redundant bot running for the rest of the life of my server).

In this instance, the commands I cared about were:

| Discord Message | Linux Command     |
|-----------------|-------------------|
| `shutdown`      | `shutdown -h now` |
| `restart`       | `reboot`          |
| `start`         | `wakeonlan`       |

The `shutdown` and `restart` commands would be sent from the bot on the Pi Zero to the server where it would proceed to run the appropriate system commands. For the `start` command, the Pi Zero sends a WakeOnLAN message to the server to turn it on. All of these messages are communicated using Go Gobs. It's a simple form of RPC for processes written in Go, and it is very easy to use.

[Here]() is the code for the Raspberry Pi bot.

All that was left was writing the code that would run on the server and listen for messages, i.e. the server controller. It's another simple Go program that reads the Gobs off the network and calls the appropriate command for the message received. The code can be found [here]().

## Setting Up Services

I wanted to set the server controller to run as a service so that it would start on boot. My first thought was to run it in a Docker container, but there's not a good way to shutdown the main computer from within a container. Instead, I looked to `systemd`. I followed [this tutorial](https://www.howtogeek.com/687970/how-to-run-a-linux-program-at-startup-with-systemd/) since I had never setup a service on Linux before, and it was quite simple. All I had to do was create a new unit file and enable the service.

## Conclusion

With this, everything was complete. I started testing the bot and server controller, quickly fixed a few issues, and finally had a working tool. I could now lay in bed with my phone, send the message `shutdown` to the bot, and have my computer shut itself down. I could just as easily send `start` and the computer would instantly fire up. No more SSH or getting up to press the power button! I have achieved laziness.
