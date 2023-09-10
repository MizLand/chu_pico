# Chu Pico - Chunithm Style Mini Controller

<img src="doc/main.jpg" width="80%">

Features:
* It's small, made for 15-16 inch screen.
* Air towers are replaced with built-in ToF sensors.
* HID lights, of course!
* 32 keys (upper and lower rows).
* Works with CrazyRedMachine's RedBoard.
* All source files open.

Thanks to many respectful guys/companies who made their tools or materials free or open source (KiCad, OnShape, InkScape, Raspberry things).

And thanks to community developers that inspired me and helped me: CrazyRedMachine (https://github.com/CrazyRedMachine), SpeedyPotato (https://github.com/speedypotato).

## Notes
This one is relatively easy to build compared with my other projects like IIDX Pico or Teeny. You can check out my other cool projects.

* Popn Pico: https://github.com/whowechina/popn_pico
* IIDX Pico: https://github.com/whowechina/iidx_pico
* IIDX Teeny: https://github.com/whowechina/iidx_teeny

This Chu Pico project:  
* Heavily depends on 3D printing, you need a Bambu 3D printer.
* Requires skills to solder tiny components.

## **Disclaimer** ##
I made this project in my personal time with no financial benefit or sponsorship. There will continue to all components and firmware to improve the project. I have done my best to ensure that everything is accurate and functional, there's always a chance that mistakes may occur. I cannot be held responsible for any loss of your time or money that may result from using this open source project. Thank you for your understanding.

## About the License
It's CC-NC. So diy for yourself and for your friend, don't make money from it.

## HOW TO BUILD
### PCB
* Go JLCPCB and make order with the gerber zip file (latest `Production\PCB\chu_main_xxx.zip`), regular FR-4 board, black color, thickness is **1.6mm**.  
* 1x Rasberry Pico Pi Pico or Pico W.  
  https://www.raspberrypi.com/products/raspberry-pi-pico
  Becareful of 3 pins that are at the other side, they're difficult to solder and may leave air bubbles.  
  <img src="doc/solder_usb_txrx.jpg" width="60%">

* 1x USB Type-C socket (918-418K2023S40001 or KH-TYPE-C-16P)
* 36x WS2812B-4020 side-facing RGB LEDs.  
  https://www.lcsc.com/product-detail/Light-Emitting-Diodes-LED_Worldsemi-WS2812B-4020_C965557.html
* TCA9548APWR (TSSOP-24) I2C multiplexer.  
  https://www.lcsc.com/product-detail/Signal-Switches-Encoders-Decoders-Multiplexers_Texas-Instruments-TCA9548APWR_C130026.html
* 3x MPR121 modules, there're many types in the market, choose ones like this, and remember to **cut (unshort) the ADDR pin** which is short by default:  
  https://www.sparkfun.com/products/retired/9695
* 5x Toshiba GP2Y0E03 ToF sensors, buy ones that equipped with cables.  
  https://www.lcsc.com/product-detail/Angle-Linear-Position-Sensors_Sharp-Microelectronics-GP2Y0E03_C920270.html
  <img src="doc/gp2y0e03_solder.jpg" width="90%">
* 2x 0603 5.1kohm resistors (R1, R2) for USB.
* 1x SN74LV1T34DBVR (SOT-23-5) level shifter (U8), if you can't find one, use a 0603 10ohm resistor (R3) as an alternative.  
  https://www.lcsc.com/product-detail/Buffer-Driver-Transceiver_Texas-Instruments-SN74LV1T34DBVR_C100024.html

  <img src="doc/pcb_1.png" width="90%">

* 8x 0603 1uF capacitors (C1 to C8), OPTIONAL, recommended.
* 10x 0603 10kohm resistors (R4 to R13) for I2C pull-up, OPTIONAL, normally not needed.

### Light Guide Panel
* Find a service to cut a light guide panel using DXF or DWG file `Production\CAD\chu_pico_lgp.*`, the size is 256mm*60mm, 1.5mm to 2.0mm thickness, thinner is better for sensitivity. 2.0mm is easy to find, 1.8mm is difficult, and 1.5mm is rare. I used 1.8mm for my build. 
  <img src="doc/lgp_1.png" width="90%">
* LGP material choices:
  * Real LGP (Light Guide Panel) material, it's the best choice.  
    <img src="doc/lgp_2.png" width="50%">
  * Clear Acrylic with Light Guide Film, it's a good choice.  
    <img src="doc/lgp_3.png" width="50%">
  * Clear Acrylic with single-side-frosted, it's a good choice.  
    <img src="doc/lgp_4.png" width="50%">
  * Clear Acrylic with manual single-side-sanding, it can work too.  
    <img src="doc/lgp_5.png" width="50%">

### PP Touch Cover
* A **textured** PP polypropylene film sheet, used as the light guide panel cover. It improves touch feel, 0.5mm thichness feels the best. If you can't find one, go get a project folder with textured cover.    
  <img src="doc/pp_1.png" width="50%">  
  <img src="doc/pp_2.png" width="80%">
* Cut the PP sheet to roughly match the shape of the light guide panel, use double-sided tape (at the edge only) to stick it on the light guide panel.

###  IR Cover
* It's for good looking, as it hides 5 ToF sensors.   
  <img src="doc/ir_cover_1.png" width="60%">
* IR lights can go through.  
  <img src="doc/ir_cover_2.png" width="60%">
* Find a service to cut an IR cover using the DXF or DWG file `Production\CAD\chu_pico_ir_cover.*`, the size is 293.2mm*63.5mm, 1mm thickness. The material must be "Infrared Transmitting Acrylic Sheet" which can block visible lights (so it looks black) while letting IR lights go through.  
  <img src="doc/ir_cover_3.png" width="80%">
* If you can't find one, cut a regular smooth surface acrylic, but it can't hide the ToF sensors which are not good looking.

### 3D Printing
* You need a Bambu 3D printer for 2 reasons:
  * Parts are designed to perfectly fit in its 256mm*256mm print bed.
  * It's AMS system works great for easy-to-remove support material.
* For all the following prints:
  * To fit object in the bed, Z rotate: 315 degree, X, Y move to: 134mm  
  <img src="doc/rotate.png" width="50%"><img src="doc/moveto.png" width="32%">  
  <img src="doc/layout.png" width="80%">
  * PLA, PETG, ABS are all OK.
  * Layer height: 0.2mm
  * 4-6 walls, 50+% infill
  * Support: Yes. If you have Bambu AMS system, use their special support material at interface layers.

* Base: `Production\3D\chu_pico_base.stl`, dark gray filament.
* Top Cover: `Production\3D\chu_pico_top_cover.stl`, dark gray filament.
* Cover Base: `Production\3D\chu_pico_cover_base.stl`, **clear transparent (IMPORTANT)** filament.
* Light Guide Panel Fixer: `Production\3D\chu_pico_lgp_fixer.stl`, color doesn't matter.

### Exploded View for Assembly
<img src="doc/assemble.png" width="80%">

From top to bottom:
* IR Cover
* Top Cover
* Cover Base
* PP Film
* Light Guide Panel
* PCB
* Light Guide Panel Fixer
* Base

You need **4x M3*12mm screws and 4x M3 hex nuts** to fix all things.

5x silicone anti-slip pads can be applied to the bottom side of the base.

### Firmware
* UF2 file is in `Production\Firmware` folder.
* For the new build, hold the BOOTSEL button while connect the USB to a PC, there will be a disk named "RPI-RP2" showed up. Drag the UF2 firmware binary file into it. That's it. There's a small hole at the bottom side of the Chu Pico, it is facing right to the BOOTSEL button.
* It works on CrazyRedMachine's RedBoard protocol. For more information, please check out CrazyRedMachine's project (Don't forget to give him a star and drop by his GitHub for other cool projects):  
https://github.com/CrazyRedMachine/RedBoard

## CAD Source File
I'm using OnShape, it's free and powerful. But it can't export original designs to local, so I can only share the link here.
https://cad.onshape.com/documents/8b9d0fe6ff1bfa4da17d33ee/w/5c7c980a282a19e7ba1db795/e/56ee65492584a3f709c23c49?renderMode=1&uiState=64fd606f17393c0e6f9b19a4
