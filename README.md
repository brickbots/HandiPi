# HandiPi

Handheld RPI4 based computer with 36-key tactile keyboard and display

![The HandiPi](https://raw.githubusercontent.com/brickbots/HandiPi/main/images/beauty/IMG_8141.jpeg)

## What is it?

Glad you asked.. it's a fully functional linux computer with:
* A Raspberry Pi 4
* Custom 36-key keyboard with 5 way directional buton based around an Atmega328
* 4.3" DSI touchscreen display
* PiSugar power controller with 5000mah battery

It runs for about 4 hours with general terminal use and is pretty useful on it's own, but you can hook 
up external monitors and other USB peripherals if you need more screen or typing space.

![Full work mode!](https://raw.githubusercontent.com/brickbots/HandiPi/main/images/beauty/IMG_8124.jpeg)

The keyboard runs QMK and interfaces to the Pi via USB, so it's fully configurable.  I really like the
[Miryoku](https://github.com/manna-harbour/miryoku) layout and use it on all my keyboards...so that's
what the physical button layout is based around.  The switches are Diptronic DTS63K tactiles with 1Nm 
of actuation force.  They look the same as the generic ones, but it's worth the few extra dollars as 
they feel so much better to type on.  It's still a thumb-typing experience, but the limited number of
keys and the well thought out layering system of Miryoku makes it a suprisingly useful keyboard!

![It's a keyboard](https://raw.githubusercontent.com/brickbots/HandiPi/main/images/beauty/IMG_8130.jpeg)

## Oh god, why?

Well.. it all started when I picked up the PCB's for the 
[PICOmputer](https://www.tindie.com/products/bobricius/picomputer-rp2040-raspbbery-pico-qwerty-devkit/) 
made by [Bobricius](https://www.tindie.com/stores/bobricius/).  It's a sort of carrier board for the 
Raspberry Pi PICO that includes a keyboard using 6mm pushbutton tactile switches and a display.  It's 
simple, but it really opens up some fun potential.  I ended up 3d printing a case for mine and adding
a battery with charging to make it a neat little toy to play with.  Along the way, I was really
impressed with how well the keyboard actually worked.. even though I didn't follow his advice and bought
cheaper switches with higher actuation force.

When it came time to replace the Orange Pi based desktop PC I used at my workbench I grabbed the RPI4 I ordered
early in the pandemic and had been hording.  I was just going to put it in a boring case, but then I got 
to thinking about the PICOmputer and wondering if I could build a case with a screen and keyboard.  I'd 
still use the computer with a monitor, keyboard and trackball at my desk most of the time, but I could 
grab it and have my workbench computer with me if I wanted to go hack at a friends house or makerspace.

So that's where the idea came from, and the rest was just balancing the screen size with portability and
thinking hard about thumb-typing layouts....

## Designing a tiny keyboard

I've built a good number of keyboards in my time, and even [designed](https://github.com/brickbots/chocV)
a [couple](https://github.com/brickbots/slabv).  Most of the keyboards I've built rely on a pre-assembled 
Pro-Micro style controller, but I just didn't think I'd have the space to use that trick here.  There are 
many good refrence designs for the basic AtMega circuit, and I can
solder surface mount diodes okay, but I realy didn't think I'd have the skills to do a fine-pitch 
AtMega surface mount package without a lot of pain and suffering.  It was then that I remembered the first
keyboard I ever built.... the [Plaid](https://github.com/hsgw/plaid)!

The Plaid is a really neat 4x12 ortho keyboard built using ALL throughhole components!  It uses virtual
usb on an AtMega328 which is one of the few AtMega versions availabe in a DIPP package.  With this 
schematic in hand and information about the boot loader HSGW used, I started designing a new PCB.

![It's a tiny keyboard](https://raw.githubusercontent.com/brickbots/HandiPi/main/images/build/IMG_4371.jpeg)

This is actually version 2... for the first one I thought I understood more than I did and left off the 3.6v
zener diodes on the USB data lines.  BTW, USB actually uses 3.6v signals!  Who knew?  I didn't know, so I 
thought the zeners were for overvoltage protection... They are not and many USB hubs/controllers won't work 
with 5v signal lines.  So, you need those if you are using a 5v MCU.

Here's a good place to thank [PCBWay](https://www.pcbway.com) for covering the cost of these boards.  Liam
reached out to me after seeing the [Framedeck project](https://github.com/brickbots/framedeck) with it's
custom keyboard/trackball PCB and asked me to give PCBWay a try with my next project.  I did, and they gave 
me a coupon to cover the cost, which was right nice of them.  The PCB's are not overly complicated, but the 
pricing was in line with other vendors, they arrived quickly, looked nice and clean and were fabbed to spec.
Overall, a nice experience and I'll definitely consider them again in the future.

So after two revisions, everything worked and it looks nice and tidy with the 1mm top PCB to cover the guts
and present nice legends.

![KB Top plate](https://raw.githubusercontent.com/brickbots/HandiPi/main/images/build/IMG_8152.jpeg)

## OS and Navigation
This little bad-boy runs Raspberry Pi OS, a Debian derivitive, and I use i3 as my window manager.  This is
a great tiling window manager that I run on all my linux systems, but it's particularly well suited for 
resource limited machines as it's very light weight.  It's also very keyboard friendly, which helps as 
this unit does not have a great pointing device.  The touchscreen works okay for some things, and the 
Miryoku layout has support for mouse keys on a layer (which can be used with hjkl or the directional button)
, but I prefer keyboard interaction where possible.

i3 does have a good number of multi-key combos to get stuff done, and these are tricky with just two thumbs. 
It's possible to get another finger in the mix and still hold on, but I ended up using the directional button 
for a lot of the multi-key directional bits like focus left/right/up/down, resizing windows, or switching
desktops.  The directions are mapped to mod-h,j,k,l which will change window focus by default.  I can combine
this shift to move windows.  If I hold down the center directional button, the four directions change
between four desktops, and I can combine this with shift to move a window to a specific desktop!

There are some other less common combos (like defining vertical/horizontal splits) that can always be 
accessed using the actual key combos

## More info

Here's a photo of the back of the unit showing the HDMI, audio output, and charging port of the PiSugar. 
To the left (in the photo, right side of the unit) is the one available USB port on the RPI 4.  To make 
the whole thing thinner, I removed the ethernet jack and double USB ports.  One of the usb pinouts is 
run internally to talk to the keyboard, and I put a single-high USB jack on the other for external 
connections.

![Connections](https://raw.githubusercontent.com/brickbots/HandiPi/main/images/beauty/IMG_8135.jpeg)

If you'd like to learn more about how this was all put together check these links below:

* [Parts List](docs/BOM.md)
* [Build Tour](docs/build.md)

## Copyright and License

Copyright (c) 2022 Richard Sutherland. All rights reserved.

All files are licensed under MIT license
see the [LICENSE](LICENSE) for more information.

