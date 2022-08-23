# Build Tour

I'm calling this a tour, not a guide, as I'm more pointing out interesting things than
giving complete instructions on how to build one of these.  I hope there might be some 
neat tricks here I can share, or at least inspire you to build something similar for yourself. 

If you want to build this exact same item, check out the [Parts List](./BOM.md)... it lists 
pretty much everything you need and there are ready-to-order gerbers and ready to print parts
in this repo. Hopefully this tour will give you enough to put it together, but I'm happy to 
answer any questions you might have.  Now on to the tour!

## Overview

![The HandiPi](https://raw.githubusercontent.com/brickbots/HandiPi/main/images/build/IMG_8178.jpeg)

I couldn't quite get all the parts in one shot, but they are all visible here.  The screen being
partially visible and blurry there in the right corner of frame.  Roughly from left to right/top
to bottom
* Bottom 3d printed case + battery double sided taped in
* Heatsink (black with thermal paste)
* 3d printed screen and keyboard bezels + keyboard PCB overlay
* Keyboard PCB assembled
* 3d printed middle layer where most everything attaches to
* RP4
* PiSugar board
* Screen

## Pi slim-down

To keep the overall thickness down, I've removed the ethernet and double-high USB jacks from
the Pi.  This is not too delicate, but be slow and careful along the way.  For more info, 
Adafruit has a nice [guide](https://learn.adafruit.com/diet-raspberry-pi) to this process.
They did a much nicer job than I did :-)

![Slim Down](https://raw.githubusercontent.com/brickbots/HandiPi/main/images/build/IMG_8155.jpeg)

I added back one single USB 2.0 port.  If you can cleanly remove the USB 3 port and solder a 
single high one back on then you are a better person than I am.  Just modify the case and you'll
have TWO external USB... one high speed!

I used the second set of USB pads from the double high jack to connect the keyboard. You can see 
this handy work, along with the crooked USB port (for shame!) here

![From the back](https://raw.githubusercontent.com/brickbots/HandiPi/main/images/build/IMG_8117.jpeg)

## PiSugar Mods

I removed the battery socket as it was too tall to fit between the PiSugar and the case.  In it's 
place I soldered two solid heavy-ish gauge wires to connect the battery.  The original power switch
is kind of tiny and hard to get to when it's all mounted.  So I desoldered that and used a nice
chunky one that is friction mounted in the bottom of the case.

![PiSugar Mods](https://raw.githubusercontent.com/brickbots/HandiPi/main/images/build/IMG_4384.jpeg)
![Battery](https://raw.githubusercontent.com/brickbots/HandiPi/main/images/build/IMG_4383.jpeg)
![Switch](https://raw.githubusercontent.com/brickbots/HandiPi/main/images/build/IMG_4382.jpeg)

I used epoxy around these mods as strain relief

## Keyboard

The keyboard has a 1.6mm double sided PCB with all the components on it, and a 1mm top plate
with no traces, just cutouts and silkscreened letters.  If you want to go stealth mode, you 
can flip it over and it's solid black!  [PCBWay](https://pcbway.com) covered the cost of these
to convince me to try them out.  I did, and they turned out great (Thanks Liam!).  The silkscreen is nice 
and sharp, which is great for the top cover.

![Keyboard](https://raw.githubusercontent.com/brickbots/HandiPi/main/images/build/IMG_4371.jpeg)

It's pretty easy to build as it's mostly through hole.  I'd suggest doing everything but the 
diodes/switches firt then flash and test before doing the surface mount diodes and finally the
switches.  Check the [schematic](./handipi_kb_schematic.pdf) for values on the components.

The elecrolytic capacitor goes on the BACK of the board as it's a bit too tall to fit well
under the keyboard cover.  There is a hole in the middle section to provide clearance.  The 
4 pin header can probably work on either side, but I put it on the bottom side and there is
a cutout in the middle section to fit the plug from the Pi.

For details about the vusb design and the specific bootloader I used, please see the 
repo for [the Plaid](https://github.com/hsgw/plaid) keyboard.  Once the bootloader 
is installed, it's standard QMK all the way.  For this specific layout, try
[Miryoku!](https://github.com/manna-harbour/miryoku)

## Case + Assembly

The case is 4 parts: middle, bottom and two top bezels. 3mf files are provided for these and I
printed them in my favorite filement, Colorfabb Ngen with a 0.6mm nozle and .3mm layer height.

### Middle

Most everything mounts to the middle (black) section.  It has M2 heat set inserts which 
faciliate all this mounting.  These 4 inserts for the keyboard are a bit longer than the middle 
is thick and protrude a bit from the bottom.  This is to allow good threading from both sides.

![Keyboard Inserts](https://raw.githubusercontent.com/brickbots/HandiPi/main/images/build/IMG_8168.jpeg)

The keyboard screws to the 'top' of these inserts and there are long stand-offs which extend down
and serve as attachment for the bottom.  There are 4 more inserts in the two upper holes, one on top
and one on the bottom.  One really long insert might work, but I didn't have one to try and two 
seemed reasonable

![Upper inserts](https://raw.githubusercontent.com/brickbots/HandiPi/main/images/build/IMG_8167.jpeg)

The screen I used had it's own threaded posts, so m3 screws secure the screen to the middle section
from the bottom.  You can see the screen here before and after mounting in these two photos.
You can also see the long stand-offs which allow attachment of the case bottom.

![Before mounting](https://raw.githubusercontent.com/brickbots/HandiPi/main/images/build/IMG_8164.jpeg)
![After mounting](https://raw.githubusercontent.com/brickbots/HandiPi/main/images/build/IMG_8161.jpeg)

Once the screen is mounted, the PiSugar and Pi4 mount to it in a sandwich along with the heatsink.  The
screen has threaded posts to mount the Pi, but the PiSugar is also threaded... I was woried I would not 
be able to get them to mate tightly, but it worked out fine without much trouble. 

![Pi + Sugar](https://raw.githubusercontent.com/brickbots/HandiPi/main/images/build/IMG_8156.jpeg)
![Pi + Sugar](https://raw.githubusercontent.com/brickbots/HandiPi/main/images/build/IMG_8155.jpeg)

My particular heatsink also screwed in to this unholy sandwich, but none of the screws I had were long
enough to go through the heatsink, PI, pisugar and thread into the screen.  So two screws hold the 
pi/sugar to the screen and the other two corner screws go through the heatsink into just the piSugar. 
It sounds janky, but it's all very tight and secure.

![Pi + Sugar](https://raw.githubusercontent.com/brickbots/HandiPi/main/images/build/IMG_8107.jpeg)

The keyboard affixes to the top side of the middle section with threaded 4mm stand-offs.  You can see
it all mounted, along with the screen, here:

![Keyboard in place](https://raw.githubusercontent.com/brickbots/HandiPi/main/images/build/IMG_8163.jpeg)

The keyboard can be tricky to plug in once it's mounted so you might want to take care of that before
screwing it down.

Once everything is mounted, double check that you have the screen plugged in and the keyboard connected
and you can move on to the bottom/bezels. 

![Double check wiring](https://raw.githubusercontent.com/brickbots/HandiPi/main/images/build/IMG_8181.jpeg)

I feel like my cat was judging my work here.....

### Bottom

Just secure the battery to the bottom of the case, clean up the print and it should fit in without any
dramas.  The switch fits into the side of the bottom case and might need some convincing.  Secure
the bottom to the middle layer with M2 bolts through the bottom into the long stand-offs.  I used hex
head bolts here to raise the bottom of the unit off the tabletop for ventilation.

## Bezels

There is a screen and keyboard bezel that tidy up the top.  They fit over the top PCB plate for the 
keyboard

![Bezels](https://raw.githubusercontent.com/brickbots/HandiPi/main/images/build/IMG_8152.jpeg)

Once you've got the bottom on, flip it over and place the printed PCB over the keyboard. 

![Keyboard cover](https://raw.githubusercontent.com/brickbots/HandiPi/main/images/build/IMG_8118.jpeg)

The keyboard bezel goes on first, and the screen bezel fits on top of it.  Then secure everything with
6 m2 screws.  I used hex head screws for the 4 around the screen to match the bottom, but I used flat
top screws for the lower ones to clear the typing path.

![You're done!](https://raw.githubusercontent.com/brickbots/HandiPi/main/images/build/IMG_4385.jpeg)

That's pretty much it!  Install the OS of your choice and happy handheld hacking!  Email if you have 
any questions or just want to share your work.

