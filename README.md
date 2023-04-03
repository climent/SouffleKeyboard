# Soufflé Keyboard

The Soufflé Keyboard is 6×4+1+4+1 keys column-staggered split keyboard with encoder support, based on the [Sofle](https://github.com/josefadamcik/SofleKeyboard) and re-inspired by the [Lily58](https://github.com/kata0510/Lily58) keyboards. It also takes a bit of layout ideas from the Kyria and the Ferris Sweep.

Soufflé was created by [Jesus Climent](https://https://github.com/climent/).

Key features:

*   Originally based on the Soufflé V1 release layout,
    *   the two pinky columns have been lowered: ~5mm for the V2, ~10mm for the V3 Sweep.
    *   the keys on the thumb cluster has been repositioned to allow for equal reach of the keys.
    *   palm key at the bottom of the outer pinkie column.
*   Choice between rotary encoder or key switch for the inner keys.
*   Redone track layout with simplified, curved tracks.
*   V3 adds support for nice!nano with solder points for a battery and a power switch. 
*   Removed i2c communication betweek halves.

The VR release is a result of me experimenting with the RGB layout. However, I could not adapt to the displaced thumb cluster, so I returned to the V1 layout when I designed the V2.

## Images of keyboard

![SouffleKeyboard PCB](docs/images/SouffleKeyboard_v2_PCB_KiCad.png)
![SouffleKeyboard V3](docs/images/SouffleKeyboard_v3.png)

## Build notes

Build guide will be added soon. Meanwhile, the [Sofle Build Guide](https://josefadamcik.github.io/SofleKeyboard/build_guide.html) should be a good starting point.

## BOM

| Item                                                       | Quantity | Notes                                                                                                                                                                                                                                                |
|------------------------------------------------------------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Soufflé PCB                                                | 2        |                                                                                                                                                                                                                                                      |
| Soufflé Plates                                             | 2+2      | Gerber files are provided to be ordered made of FR4. Can be 3D printed, extruding the upper plate at 1.5mm, the lower at a minimum of 1.5mm.                                                                                                         |
| Pro Micro pin MCU, or equivalent.                          | 2        | RP2040 recomended. Alternatives: Pro Micro (or clone), Elite-C, Elite-Pi, Frood, Liatris, nice!nano (for BT wireless)                                                                                                                                |
| 1N4148 Diodes                                              | 60       |                                                                                                                                                                                                                                                      |
| Kailh MX hotswap switch sockets                            | 60       |                                                                                                                                                                                                                                                      |
| MX switches                                                | 60       |                                                                                                                                                                                                                                                      |
| 1u keycaps                                                 | 60       |                                                                                                                                                                                                                                                      |
| M2, 7 mm brass (or other material) spacers                 | 10       | These are the optimal spacers. Longer ones work, too, but with 7mm the gap is minimal.                                                                                                                                                               |
| M2x0.4mm, 5mm length flat head screws                      | 20       |                                                                                                                                                                                                                                                      |
| M2x0.4mm, 7mm length flat head screws                      | 4        | If using OLED screen plexiglass protectors.                                                                                                                                                                                                          |
| PJ-320A TRRS 3.5mm Audio Jack Connector Through Holes      | 2        | Not necessary if you are using wireless, via nice!nano.                                                                                                                                                                                              |
| Surface Momentary Tact Switch, 3mm x 4mm x 4.3mm           | 2        |                                                                                                                                                                                                                                                      |
| 2.54mm Round Hole Male Tin Gold Female Pin Headers, 40p    | 2 (opt)  | HIGHLY RECOMMENDED. However, If you want to solder the MCU directly to the board, these are not necessary.                                                                                                                                           |
| Mill Max socket pins                                       | 48 (opt) | Add 8 extra for the OLED screen, if used. Alternatively, socketing can also be done with diode legs.                                                                                                                                                 |
| 1.25u keycaps                                              | 2 (opt)  | Alternative to 2x 1u keycaps.                                                                                                                                                                                                                        |
| SSD1306 128x64 OLED                                        | 2 (opt)  |                                                                                                                                                                                                                                                      |
| EC11 Encoder                                               | 2 (opt)  | Optional, as the board allows for either 2x encoders or switches.                                                                                                                                                                                    |
| Encoder knob, 16mm                                         | 2 (opt)  | If encoders are used.                                                                                                                                                                                                                                |
| M2, 10 mm brass (or other material) spacers                | 4 (opt)  | If using OLED screen plexiglass protectors.                                                                                                                                                                                                          |
| MSK12C02 power switches                                    | 2        | If using nice!nano MCUs and batteries, for BT wireless.                                                                                                                                                                                              |
| Battery, 10mAH                                             | 2        | If using nice!nano MCUs and batteries, for BT wireless.                                                                                                                                                                                              |
| TRRS audio cable, for connecting both sides                | 1 (opt)  | Not necessary if you are using BT wireless, via nice!nano.                                                                                                                                                                                           |

## Firmware 

Soufflé uses [QMK firmware](https://qmk.fm/) and it is fully compatible with the Sofle firmware.

## Default layout 

Soufflé uses a similar layout than the Sofle, with a full 6x5 matrix, and the encoders connected to the same pins. The main difference is the position of the outermost thumb key, which has been moved to the bottom of the pinky column, to be used with the palm.

## Older versions

In this repository you will find several  releases of the Soufflé Keyboard:

*   V1: Based on the Sofle v1 and the Lily58. Key features:
    *   Added the palm key at the bottom of the pinky column.
    *   Some re-routing done and some label fixes, but modtly unchanged from the Sofle v1.
*   VR: Based on the Sofle RGB. Key features:
    *   Same palm key configuration as the V1.
    *   The layout footprint is based on the RGB, and thus the thumb cluster is slightly displaced to the center (compared to the V1).
    *   The encoder footprint shares a switch footprint, allowing for the user to choose what to put there.
    *   Pins for the encoder/switch have been exposed, as the top case plate can accommodate a roller encoder.
*   V2: Based on the Soufflé V1. Key features:
    *   Same palm key configuration as the V1.
    *   Pinkie columns have been lowered.
    *   Thumb cluster repositioned, to make the keys slightly more accessible.
    *   The encoder footprint shares a switch footprint, allowing to choose what to put there.
    *   Removed I2C connectivity option.
    *   Curved contour of the keyboard.
*   V3: Based on the Soufflé V2, and the Ferris Sweep layout. Key features:
    *   Same palm key configuration as the previous releases.
    *   Pinkie columns have been lowered even further, similar to the Ferris Sweep keyboard.
    *   Middle finger column has been raised, similar to the Ferris Sweep keyboard.
    *   Thumb cluster repositioned, to make the keys slightly more accessible, as the V2.
    *   The encoder footprint shares a switch footprint, allowing to choose what to put there, as the V2.
    *   The reset button has been repositioned, and is accessible through a hole in the lower plate.
    *   Added battery connection points, and a power switch, for use with nice!nano.
    *   Removed I2C connectivity option.
    *   Curved contour of the keyboard.
