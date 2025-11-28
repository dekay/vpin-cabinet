<!-- Note to self: Github markdown supports comments -->
<!-- Github docs support five callouts: > [!NOTE], [!TIP], [!IMPORTANT], [!WARNING], [!CAUTION] -->

# A FreeCAD Model of a Virtual Pinball Cabinet

> [!WARNING]
> **Use at your own risk**. The wood has been cut but I have not built this cabinet as of yet. There are some things I know need to be fixed and what is almost certainly other surprises waiting for me to discover. Having said that, it seems to be hanging together *really well* so far.

## Description

This is a relatively complete model of a full scale Williams' standard body pinball cabinet (20.5 inches of internal width) adapted for use as a virtual pinball cabinet. It is designed around these components:

- an LG C2 42" OLED television as the main playfield display. Newer LG C-series TV's have very similar dimensions and could likely be used as well with little to no modifications. You'll need to either [decase the TV](https://www.vpforums.org/index.php?showtopic=51446) or cut away the bump for its IR Receiver so it will fit.
- an HP Z30i 30" LCD Monitor for the translite display. I went this route because its 4:3 display ratio is a very close match to that of a real translite. The backbox is standard width so you could fit a smaller but more modern 16:9 1080p display in there as well.
- a bare [15.6 LP156WF6-SPB1 1080p LCD display](https://www.aliexpress.com/item/1005004859062249.html) with [compatible controller](https://www.aliexpress.com/item/4001312799490.html). Any display of this size would work. I chose this one after some research because it has excellent color, brightness, and off-angle viewing.

## Features

Design features include:
- Measurements taken from real pinball parts where possible! I got my parts from the good folks at [Pinball Life](https://www.pinballlife.com/) and would recommend them. Their prices are good, their selection is great, and their support is excellent. My siderails were bent in shipping and they sent me a new set right away.
- Pocket-hole based construction with 1" x 1" glue blocks providing additional strength. The glue blocks on the bottom of the cabinet have a routed channel that the undercab LEDs can fit in to. That prevents the LEDs from being crushed should the cabinet ever be set on the ground or a bench without the legs on.
- Routed slots on the left and right sides of the cabinet to make room for the LG C2 and its support that would not otherwise fit.
- Surround Sound Feedback (SSF) based on two Dayton BST-1 shakers and four Dayton HDN-8 exciters driven by three [ZK-TB21 amplifiers](https://www.aliexpress.com/item/1005007089986162.html) that are in turn connected to the popular StarTech 7.1 USB Audio Adapter
- A high density LED matrix built up from three [32x16 WS2812B panels](https://www.aliexpress.com/item/4000939714620.html). The matrix is attached to the playfield TV mount that is on a pivot rod, allowing the entire playfield to rotate for access to the cab internals
- Rear doors for the backbox and cabinet, with a pull-out computer shelf that slides out from the latter
- "Floating" power and audio shelves. The shelves are not screwed into either side of the cabinet. Rather, they have three blocks on either side to keep them in place with foam weatherstrip so they don't slide around and vibrate. This floating design should in theory improve SSF performance by allowing the sides of the cabinet to vibrate more freely without the shelves pinning them down.
- [Cable raceways](https://www.amazon.ca/dp/B0CRH53YQP) to help keep the wiring nice and clean
- A plywood cut plan. You'll need one sheet of 3/4" and one sheet of 1/2". This is *just* enough as I've included pieces like the playfield monitor support and translite monitor support that mjr does not include in his plans.

> [!NOTE]
> The model doesn't show 100% of these features accurately at the present time but it will get there eventually.

## Goals

One of my goals in this project was to minimize borders around the various displays. Stepping up to a widebody design would have made things a lot easier in terms of fitting the playfield with those extra three inches or so to play width. But I didn't like the idea of those borders on either side and LED strips can only fill so much space. Similarly, the HP 30" 4:3 monitor *barely* fits uncased within the standard backbox width. The speaker panel is also a game of millimeters: the taller 4:3 display means less room for the speaker panel below.

I'm also a symmetry freak. For example, the bottom bezel of the LG C2 is 10mm vs the 6mm on the other three sizes. I've chosen to center the displayable area in the cab and not the monitor itself. This makes more work but it is going to look *great*: the displayable area lines up with the cabinet siderails almost perfectly. Another example is the speaker panels, where I'm trying to make the rectangular cutouts as wide as possible to show the LED effects off better while at the same time keeping even spacing between everything on there.

This model is built using FreeCAD 1.1dev from fall 2025. It should still open up on older version (like 1.0.2 stable as of time of writing) but you might see a lot of errors spew in the console.

# Known issues and TO-DOs

## Known Issues

### Plywood is Hard

> [!IMPORTANT]
> This one is a biggie

Being the noob woodworker that I am, I blithely assumed that 3/4" thick plywood is 3/4" thick and that 1/2" plywood is (suspenseful music plays) 1/2" thick. It isn't. 3/4" plywood where I live is actually 18mm thick (0.707") and 1/2" is 11.8mm thick (0.464" thick). And this, I realized later, is why mjr's plans have his cabinet at 20.5" wide on the inside but only 21 7/8" wide on the outside. Grrrr. Currently this discrepancy is baked into the model everywhere except the speaker panel and it will take a fair bit of effort to clean it up. In the meantime, that discrepancy hits in the following ways:

- the sides of the backbox will be too long by about 0.083. It doesn't sound like much but that is well over a 16th of an inch
- some other places I can't remember right now :-(

### FreeCAD Foibles

FreeCAD can be a bit, shall we say, rough around the edges. Version 1.0 was a bit of a watershed release with major improvements to the toponaming problem (TNP) that you might have heard about, UI cleanups, etc. *Buuuuuut* if you don't do some things "the FreeCAD way", it might come back to bite you later. These "ways" aren't always obvious nor enforced. My big "oops" was to create a Clone of some Body, and then move that Clone out of its associated Body into another Part. Why? Because the only thing that Body contained was the Clone, so why not simplify things a bit?

Because FreeCAD hates it when you do that, that's why. 

I couldn't figure out why I couldn't reliably use the Transform tool on these Clones. At one point, trying to do so would actually crash FreeCAD. Now there are some guardrails in place to at least prevent those crashes, but these Bodyless Clones still exist in the model. Trying to use the Transform tool on them to move them around probably won't work. The solution is to tediously go through the model and put these Clones in their own Bodies, but that is a job for another day.

Besides the above, the parts of the model I added to what I was given look like something done by somebody that was learning FreeCAD as they went. That's because I was learning FreeCAD as I went. There's some bits I've built up that are definitely cringeworthy looking back but they are perfectly serviceable for now. I also used the model to learn new techniques along the way, and some of the resulting bits like the 120mm fans and the bass shakers look pretty cool.

## Model TO-DOs

- The backbox hinges don't currently line up with the metal plate above it inside the backbox
- Verify height of leg brackets because of glue blocks
- Change shelf supports to the floating design and remove the shock absorbing material currently under the shelf
- Clean up power shelf
- Show LEDs behind cabinet
- Finalize sub design. Currently 8". Move to 6" and put in a tuned box for better sound?
- Consider channels for LED strips
- Figure out final mounting of playfield LEDs.
- Finalize how the backbox speakers will be fastened. They can't continue to be suspended in free space.
- I think my coin door cutout is a wee bit too high. Check into this

## Documentation TO-DOs

- Link to more of the parts I've used
- Write up some resources on learning FreeCAD
- Add some images of this thing!!!

# Shout-Outs & Credits

## Shout-Outs

The design is heavily influenced by [@mjr](https://github.com/mjrgh/)'s phenomenal [Pinscape Build Guide Version 2](http://mjrnet.org/pinscape/BuildGuideV2/BuildGuide.php). Many folks in the vpin community refer to it as "The Bible" for good reason.

[Way of the Wrench](https://www.youtube.com/@wayofthewrench)'s incredible [Virtual Pinball Cabinet Budget Build Series](https://www.youtube.com/watch?v=JxilHoceiNo&list=PLrqlHbqP7FIO5P8e8HtrBB01xqQtAWpJ5) on Youtube was another major influence. While WotW based his cabinet off mjr's work, I'd have been lost without the tips, tricks, and techniques taught in this series.

The good folks on the VPX Discord also deserve tons of credit for sharing their designs, advice, and ideas along the way. Similarly, this whole thing would be pointless without the incredible effort the software developers and table authors put in that have made virtual pinball so great.

## Credits

This work builds upon a model originally developed by [GaM3r2Xtreme](https://github.com/GaM3r2Xtreme) and provided to me on the Virtual Pinball Discord. I had always planned to develop a cabinet model before I started cutting plywood but the head start their model gave me was *huge*. I was able to jump right in and start adding detail based on what I gleaned from the work already done.

# License

[![CC BY-NC-SA 4.0][cc-by-nc-sa-shield]][cc-by-nc-sa]

This work is licensed under a
[Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License][cc-by-nc-sa]. Permission is granted to remix, tweak, and build upon this work non-commercially, as long as you credit [GaM3r2Xtreme](https://github.com/GaM3r2Xtreme) as the original author and license your creation under the identical terms.

[![CC BY-NC-SA 4.0][cc-by-nc-sa-image]][cc-by-nc-sa]

[cc-by-nc-sa]: http://creativecommons.org/licenses/by-nc-sa/4.0/
[cc-by-nc-sa-image]: https://licensebuttons.net/l/by-nc-sa/4.0/88x31.png
[cc-by-nc-sa-shield]: https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg
