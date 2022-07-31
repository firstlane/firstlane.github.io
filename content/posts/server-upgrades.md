---
title: "Server Upgrades"
date: 2022-03-12T20:42:00-06:00
---

I've been enjoying having a home server setup, but I was facing a problem. In a previous post, I wrote about a Discord bot I wrote to allow me to start and shutdown my server easily. The motivation for this was that the server was loud, and in my bedroom. I wanted to be able to shut it down easily if I was laying in bed and ready to fall asleep.

This functionality is useful, but it defeats the purpose of having a server. They're typically meant to run 24/7. Also, I've been looking at setting up a backup solution using rsync or borg, and the first backup is likely to take hours. I don't want to turn off the server in the middle of the night when it might be running a backup.

I started looking at where else I could put my server. The only place that made sense was in the room outside my bedroom. It would be within reach of my modem so I could hardwire it. The only issue was my cat. He likes to chew through wires, and has damaged a decent amount of equipment in the past. I looked at enclosures online but thought they were too pricey. However, I came across some DIY server rack builds and thought it looked like a fun project. And so, I set out to build my own enclosure.

I started by taking a reference image from online and modeled it in Blender, using the dimensions of my computer for reference. I wanted the enclosure to comfortably hold my computer, while also having some extra storage for a couple of Raspberry Pis, a network switch, etc. I ended up modeling a small shelf above the computer to hold those items. You can see the model below.

After I was satisfied with the model, I wrote up a list of materials I'd need from Home Depot and got everything purchased. After that, I spent the weekend cutting wood, drilling holes, and putting the enclosure together.

I initially wanted to do a clear acrylic panel for the front door of the enclosure. I had thought of putting some LED strips or a smart color bulb inside the rack, and I wanted to be able to see them nice and clear. When I got to this part of the build, I was sorely disappointed. I didn't have proper tools to cut acrylic, and the panel ended up getting cracked in multiple places. It was essentially useless at that point, since I didn't want to have myself or my cats cutting ourselves on the enclosure. For future reference, use a circular saw for cutting acrylic, not a hand blade :)

I settled on using some leftover MDF board for the door. The last touch was adding some cage wire around the enclosure openings. I decided to go with this instead of more MDF boards to allow air into the enclosure. The wire would definitely be strong enough to keep my cats out.

After getting the enclosure setup in my house and the computer moved inside it, I ran some ethernet cable in conduit to keep it protected and got everything fired up. My bedroom is now silent when I go to sleep, and I have a server running 24/7.
