---
layout: default
title: Soufflé Keyboard - build guide (v3)
---

This guide is for the V3 (Sweep release) of the Soufflé keyboard, but it can serve as a base guide for any other Soufflé revision.

If you don't have all the necessary parts, please read about [how to source the parts][sourcing].

## Bill of materials

The following is needed to build the keyboard. You can find [links for the most of the components in the sourcing parts section][sourcing].

- **2 PCBs** (see [sourcing][sourcing])
- **2 top plates**, **2 bottom plates** for a sandvich-case build. (see [sourcing][sourcing])
- **58-60 keyboard switch sockets by Kailh**. The PCB supports only MX switches. A Choc version of the Soufflé keyboard will be available some time in the future. They are available on Aliexpress, Splitkb.com and others. 
- **58-60 keyboard MX switches** of your preference.
- **58-60 keycaps**. You can use either all in `1u` size but it looks nicer with two `1.5u` for the thumb keys.
- **58-60 diodes  1N4148W**. They are surface mount diodes in SOD123 package.
- **2 TRRS connectors**. The same type which is used for Corne, Lily58 etc.
- **2 tactile buttons** through-hole, 2 pins. Technically optional: you can use metal tweezers whenever you need to reset the microcontroller.
- **1 TRRS cable**. TRS should work.
- **10 7mm M2 spacers**. They will hold the bottom and the top together. 
- **4 10mm M2 spacers**. Needed to hold transparent OLED cover but even though there are mounting holes in the PCB.
- **20 (+8) 5mm M2 screws**. 20 are going to hold the boards together (via spacers).
- **10 adhesive rubber feet**. They are really important, trust me.
- **0-2 ssd1306 128x32 OLED display module**. Very common everywhere. 
- **2 OLED covers** Optional. OLED cover should be cut from transparent acrylic. Source file for [version 1 is avalalble in the Sofle repostiory](https://github.com/josefadamcik/SofleKeyboard/tree/master/Sofle_v1/Case).
- **0-2 Rotary encoders EC11**, optional. The Soufflé is ready to accept either switches or encoders in one position.
- **A matching knob** for each encoder. 
- **2 Pro Micro** board or clone. With 2x12 pins. Just make sure you **don't** buy something like Arduino Micro (a different pinout) or Arduino Mini (different microcontroller). You could also use Elite-C which in basically a Pro Micro with USB-C. New microcontrollers based on the Raspberry Pico (rp2040) are available, and have more memory.
- **4x12 pin header (and optionally socket)** for Pro Micros. There are several ways how to mount Pro Micros to the board. Either the male PIN headers you most likely got with the board from the supplier could be used to solder it directly to the board. Build guides for Helix, Corne and Lily58 suggest [those spring pin headers][springpinheader] which are very compact and give you non-permanent connection (you can remove or replace Pro Micros). Another possible approach [is described at splitkb.com][promicrosocketing].
- **2x4 pin header (and optionally socket)** for OLEDs. I have used the most common 1x4 female pin sockets which are quite tall but they also fit the height of ProMicro with the sockets I have used. Unfortunately, the pin headers on my OLED modules (again those very common square male headers you would get with the modules) are loose in the sockets. It works but it's fiddly. I'll have to find a better solution.
- **USB Cable** to connect the keyboard to a computer. As a favourite, I use magnetic cables, to avoid putting too much stress into the USB connector.

![SouffléKeyboard parts](images/build_guide/parts.jpg)

That's it. There are no RGB LEDs on the board. But if you really need underglow it is be possible to connect an RGB LED strip since there are 3 pads (VCC, GND and data) on the board. You would need to add support to the firmware on your own.

## Tools and materials

- soldering iron
- solder wire
- good tweezers, preferably non-magnetic
- masking tape
- isopropyl-alcohol for cleaning 
- screwdriver

## Warnings and disclaimers

- Think twice, solder once. Desoldering is frustrating and it's easy to mess up things.
- Don't connect or disconnect the TRRS cable when the keyboard is powered. It may short out. Always disconnect the USB cable first.
- If you are not using magnetic cables, be gentle with the USB on your microcontroller. They are easy to break.

## Steps

### Prepare

![Step 1](images/build_guide/step1.jpg)

Make sure you have all the right parts for the keyboard, specially the PCB and the top and bottom plates match. Some people mark the top/bottom of the keyboard with masking tape. I owrk with both PCBs at the same time, thus making sure I am soldering the right side on both PCBs.

### Components on the backside 

![Step 2.1](images/build_guide/step2.1.jpg)
![Step 2.2](images/build_guide/step2.2.jpg)

Only if you are using, or plan to use, nice!nano microcontrollers.

Start with the power switches. Place them on the bottom side of the boards, and solder the pins to the PCB.

Next step is the diodes. They go on the backside of the PCB. Make sure you have orientation right. The end with the thin line is Cathode (-) and it should go in the direction of the "arrow" symbol on the PCB.

![Step 3.1](images/build_guide/step3.1.jpg)
![Step 3.2](images/build_guide/step3.2.jpg)

Add a bit of solder wire to one of the two diode pads on every diode footprint of both boards. This way you can then solder one of the diode's side without needing 3 hands: one for the solder iron, one for the diode, and one for the solder wire. Use the antimagnetic tweezers to hold the diode while re-heating the solder paste on the pad, and making sure you place the diode with the correct orientation.

![Step 3.3](images/build_guide/step3.3.jpg)
![Step 3.5](images/build_guide/step3.4.jpg)
![Step 3.4](images/build_guide/step3.5.jpg)

Finally, solder the other pad and complete the diodes on both sides.

![Step 4.1](images/build_guide/step4.1.jpg)

The sockets for the switches belong again on the back side, the same side as diodes. Make sure they are flush with PCB. Watch the markings on the silkscreen which show the correct orientation.

![Step 4.2](images/build_guide/step4.2.jpg)

Soldering one pad of the socket for all the sockets at once, approaching the sockets from the same side, makes it easier to work with them. Once one side is soldered, turn around the PCB and solder the other pad.

![Step 4.3](images/build_guide/step4.3.jpg)

A way to keep the MX sockets in place while soldering them is by using the switches. Put the switches in place (upper side of the PCB), and add the sockets to the bottom side. Now soldering sould be easier.

![Step 4.4](images/build_guide/step4.4.jpg)
![Step 4.5](images/build_guide/step4.5.jpg)

### Components on the front side

![Turn the PCBs around](images/build_guide/step4.6.jpg)

![Step 5](images/build_guide/step5.jpg )

Solder the jumper pads for the OLED on the top side of the PCB.

![Step 6.1](images/build_guide/step6.1.jpg)
![Step 6.2](images/build_guide/step6.2.jpg)

If you are using sockets for the microcontrollers, place them on each side covering the marked rectangle. This way the microcontroller will go face down.

Although sockets are optional, I encourage you to use them. If you solder the microcontrollers directly to the PCB and there are problems with them, you will have a hard time desoldering them.

Note: if for whatever reason you want to place the microcontrollers with the chip facing up (some boards come with LEDs, or boot/reset switches on the upper side, or you are planning to place a small battery under the microcontroller, and want to avoid the chip and the components using that space), you can place the sockets on the non-marked pin holes.

![Step 6.3](images/build_guide/step6.3.jpg)

Some people use masking tape to keep the sockets in place. I instead follow this process: I solder a single pin on one end of the socket. Once that pin is soldered, I reheat the solder while settling the socket with my thumb. This way I make sure the socket is push all the way through and at the right angle. Then I solder the pin on the other side. Then I reheat the pin with the soldering iron while I push the socket to make sure is completely pushed to the right location. I then proceed to solder all the other pins.

Solder the socket pins from the bottom side, making sure the solder does not overflow to the other pin holes. If the solder overflows, you will need to remove it, as that will short the connections to the switches. 

![Step 7.1](images/build_guide/step7.1.jpg )

TRRS sockets go on the top. Use a piece of masking tape to fix them and apply solder from the bottom side.

![Step 7.2](images/build_guide/step7.2.jpg )

Reset switches go either on the bottom side (there is a hole in the bottom plate to access the switches), or you can place them on the top, if you don't plan to use plexiglass protectors. In any case, solder from the opposite side.

![Step 8](images/build_guide/step8.jpg )

Finally place the 4-pin socket for the display, keep it in place with masking tape (or repeat the procedure I follow, soldering a single pin and correcting the placement while heating the pin, etc), and solder it. In this picture you can see I have used medium profile sockets for the microcontroller so that a battery fits under it, and i have soldered a low profile socket and added a medium profile socket on top. This way the OLED screen can rest on top of the microcontroller, after you make sure you add some kapton tape (or other form of isolation) to avoid shorting the micro. There are other options out there to keep the OLED above the micro, like higher sockets.

### Pro Micro and display pins

![Step 9.1](images/build_guide/TODO.jpg )

There are several ways how to connect the microcontrollers to the boards. You can solder them directly to the PCB, using headers (you most likely received them with the micros). Once again, I encourage you NOT to do that. I have had instances in which the micro was faulty and it would have been a nightmare to desolder it and resolder a new one.

If you use sockets, I have used component "legs", similar to what you can find in this [Splitkb article](https://docs.splitkb.com/hc/en-us/articles/360011263059). However I prefer using Mil Max rounded pins, as they are stronger.

**Keep in mind the orientation**. If you placed the sockets (on the upper side of the PCBs) over the rectangles, the microcontrollers are placed face down.

I usually place the Mil Max pins on the sockets, place some masking tape (to avoid the solder reaching the socket, and thus making it impossible to remove the micro), place the micro on top, and solder the pins.

Follow the same process for the OLED displays, if you are using any.

### First test

![Step 9.2](images/build_guide/TODO.jpg )

Now it is already possible to connect the microcontrollers and OLED displays to the boards, flash the firmware and check if all keys work using a piece of wire or tweezers, shorting all the pads on the switch sockets.

### Rotary encoders

![Step 10](images/build_guide/step10.jpg )

Both halves assembled, a rotary encoder can be added on both, one or none. I have also cleaned flux residue from the back side using some isopropyl alcohol, cotton buds and paper towels.

### Keyboard switches and plates

![Step 14](images/build_guide/IMG_20191109_154009.jpg )

Snap first switches into corners.

![Step 15](images/build_guide/IMG_20191109_160157.jpg )

Mount the stand-offs to the top plate.

![Step 16](images/build_guide/IMG_20191109_160519.jpg )

Carefully snap the first switches to the sockets. Be careful so you don't bend their contacts. Add more.

![Step 17](images/build_guide/IMG_20191109_160802.jpg )

Until they are all in place.

![Step 18](images/build_guide/IMG_20191109_160811.jpg )

Double-check the bottom. You should see all the contacts in sockets.

![Step 19](images/build_guide/IMG_20191109_161014.jpg )

And mount the bottom plate.

![Step 20](images/build_guide/IMG_20191109_161224.jpg )

Completed half of the keyboard waiting for keycaps.

### Finishing touches

![Step 21](images/build_guide/IMG_20191109_163910.jpg )

Put at least 4 adhesive rubber feet in the corners so the keyboard is not sliding over your desk when you type.

## Warnings and disclaimers

- Don't connect or disconnect the TRRS cable when the keyboard is powered. It may short out. Always disconnect the USB cable first.
- If you are using microcontrollers with micro USB ports and not using magnetic cables, be gentle when you connect and disconnect your USB cable. They connectors are really easy to break.

## Firmware and programming

Soufflé keyboard uses [QMK Firmware][qmk_firmware], and uses the same connections than the [Sofle keyboard rev1](https://github.com/josefadamcik/SofleKeyboard/tree/master/Sofle_v1). Support for the board is part of the [main QMK repository](https://github.com/qmk/qmk_firmware/tree/master/keyboards/sofle/rev1). There's also a basic support in [QMK Configurator][qmk_configurator].

The best approach is to build the firmware yourself. You should be familiar with QMK and be able to make it work on your local environment. If not, please [follow the instructions in the documentation][qmkintro].

- Make sure your QMK environment [is setup][qmkintro].
- Make sure halves are not connected together with TRRS cable.
- Connect one half to USB, flash the firmware (always follow the actual instructions in the QMK documentation! The command might look something like this: `qmk flash -kb sofle/rev1 -km default`). Use the reset button to reset the keyboard when you are asked to in the console. 
- Connect the second half and flash it in the same way as the previous one.
- Disconnect the USB cable. Connect both halves together with your TRRS cable.
- Connect the USB cable to the **left** side[^1]. 
- Enjoy!

## Troubleshooting

## Modifications

## Links

- [Github with KiCad projects for the original Sofle][soflegithub]
- [Layout in KeyboardLayout editor][soflelayout]
- [QMK Firmware][qmk_firmware]
- [QMK Configurator][qmk_configurator]

## Footnotes

[^1]: This can be changed, look for [setting handednesss][qmkhandedness] in QMK documentation.

[layoutarticle]: <https://josef-adamcik.cz/electronics/in-search-of-the-best-custom-keyboard-layout.html> "In search of the best custom keyboard layout"
[introductionarticle]: <https://josef-adamcik.cz/electronics/let-me-introduce-you-sofle-keyboard-split-keyboard-based-on-lily58.html> "Let me introduce you SofleKeyboard - a split keyboard based on Lily58 and Crkbd"
[soflelayout]: http://www.keyboard-layout-editor.com/#/gists/76efb423a46cbbea75465cb468eef7ff "Sofle Keyboard layout at keyboard-layout-editor.com"
[soflegerber]: https://github.com/josefadamcik/SofleKeyboard/releases "SofleKeyboard - gerber files"
[qmk_firmware]: https://github.com/qmk/qmk_firmware/ "QMK firmware"
[qmk_configurator]: https://config.qmk.fm/#/sofle/rev1/LAYOUT "QMK configurator"
[springpinheader]: <https://yushakobo.jp/shop/a01mc-00/> "Spring pin headers - Japaneese"
[qmkprotonc]: https://qmk.fm/proton-c/ "QMK Proton-C"
[promicrosocketing]: <https://docs.splitkb.com/hc/en-us/articles/360011263059> "How do I socket a microcontroller? by splitkb.com"
[qmkintro]: <https://beta.docs.qmk.fm/tutorial/newbs_getting_started> "QMK getting started"
[qmkhandedness]: <https://docs.qmk.fm/#/feature_split_keyboard?id=setting-handedness> "QMK firmware - setting handedness"
[manufacturingproblems]: https://josef-adamcik.cz/electronics/corne-keyboard-build-log.html#manufacturing-at-jlcpcb---update-27112019 "Possible problems when manufacturing top plate for Corne"
[nooledlag]: https://github.com/qmk/qmk_firmware/issues/7522 "No OLED lag bug"
[soflegithub]: https://github.com/josefadamcik/SofleKeyboard "SofleKeyboard - KiCad project on Github.com"
[sourcing]: <{{ site.baseurl }}/sourcing_parts.html> "Sourcing parts"
[rgbbuildguide]: <{{ site.baseurl }}/build_guide_rgb.html> "Sofle RGB build guide"
[chocbuildguide]: <{{ site.baseurl }}/build_guide_choc.html> "Sofle Choc build guide"
