# Nintendo Entertainment System (NES) Discrete Mapper Cartridge

This is an updated design of my old <a href="https://mousebitelabs.com/2020/09/11/nes-reproduction-quick-guide-custom-pcb/">NES Discrete cartridge boards</a>. Functionally, this design is nearly the same as the older one, but I added compatibility for a few new mappers and expanded the available memory for some mapper types, and under the hood I have ported the project over from Eagle to KiCad and heavily cleaned up the schematic and some of the trace routings. This version is also fully open source!

![mage](https://github.com/user-attachments/assets/f5ad6fda-808d-47ae-aa16-ad9cfb6507dc)
![mage](https://github.com/user-attachments/assets/2e692194-2ee1-4457-96f9-8d83b99148e9)


This circuit board can be used to make most NES cartridges that rely on discrete logic chips to operate. These boards are most common in the earlier NES releases. The following mapper types are supported (click the link to view the games that use that specific mapper):

| Board        | Mapper | Example Game                  | Database Link                                                                                  |
| ------------ | ------ | ----------------------------- | ---------------------------------------------------------------------------------------------- |
| NROM         | 0      | Balloon Fight                 | [https://nescartdb.com/search/advanced?ines=0](https://nescartdb.com/search/advanced?ines=0)   |
| UxROM        | 2      | Castlevania                   | [https://nescartdb.com/search/advanced?ines=2](https://nescartdb.com/search/advanced?ines=2)   |
| CNROM        | 3      | Paperboy                      | [https://nescartdb.com/search/advanced?ines=3](https://nescartdb.com/search/advanced?ines=3)   |
| AxROM        | 7      | Battletoads                   | [https://nescartdb.com/search/advanced?ines=7](https://nescartdb.com/search/advanced?ines=7)   |
| Color Dreams | 11     | Bible Adventures              | [https://nescartdb.com/search/advanced?ines=11](https://nescartdb.com/search/advanced?ines=11) |
| BNROM        | 34     | Deadly Towers                 | [https://nescartdb.com/search/advanced?ines=34](https://nescartdb.com/search/advanced?ines=34) |
| GNROM        | 66     | Super Mario Bros. / Duck Hunt | [https://nescartdb.com/search/advanced?ines=66](https://nescartdb.com/search/advanced?ines=66) |

There are a handful of more obscure mappers supported as well:

| Board            | Mapper | Example Game        | Wiki Link                                                                                  |
| ---------------- | ------ | ------------------- | ------------------------------------------------------------------------------------------ |
| CNROM (Panesian) | 3      | Bubble Bath Babes   | https://www.nesdev.org/wiki/Oversize                                                       |
| NINA-03/-06      | 79     | Krazy Kreatures     | https://www.nesdev.org/wiki/NINA-003-006                                                   |
| JF-xx            | 87     | The Goonies (JPN)   | https://www.nesdev.org/wiki/INES_Mapper_087                                                |
| SA-008-A, 800008 | 148    | Tetris (Tengen)     | [https://www.nesdev.org/wiki/INES_Mapper_148](https://www.nesdev.org/wiki/INES_Mapper_148) |
| UNROM (Modified) | 180    | Crazy Climber (JPN) | [https://www.nesdev.org/wiki/INES_Mapper_180](https://www.nesdev.org/wiki/INES_Mapper_180) |

## Important Things Before You Start

1) <a href="https://github.com/MouseBiteLabs/NES-Cartridges/wiki">Please review the wiki for more information about using the circuit boards, instructions for how to program them, and example builds.</a>
2) When soldering parts on, it's a good idea to put kapton tape or otherwise cover the bottom cartridge edge. You do not want to get solder on the cartridge contacts.
3) I am not responsible for any damage you do to your self or your property. Attempt this project at your own risk.
4) I do not guarantee design compatibility. You may encounter issues with certain games. There is also a chance I have made an error in the design or the BOM - if this is the case, I will do everything I can to address the problem as quickly as possible.
5) If you are using this board to make games other than for personal use, you must have permission from the originator to use and distribute any ROM images or other related material. You are responsible for making sure you adhere to any license requirements.

DO NOT use my circuit boards for profiting from stolen work - this especially includes homebrew content, ROM hacks, and using fan-made labels without permission from the originator. **Support ALL original creators!**

## Board Characteristics and Order Information

The zipped folder contains all the gerber files for this board. The following options **must** be chosen when ordering boards for yourself.

- Thickness: 1.2mm
- Surface Finish: ENIG
- Gold Fingers: Yes, 30° chamfer

**I sell this blank circuit board on Etsy, so you don't have to buy a bunch of multiples if you don't want to.** (Click the banner!)

(NOT YET LIVE)

<a href="https://mousebitelabs.etsy.com/"><img src="https://github-production-user-asset-6210df.s3.amazonaws.com/97127539/239718536-5c9aefe3-0628-4434-b8d8-55ff80ac3bbc.png" alt="PCB from Etsy" /></a> 

You can use the zipped folder at any board fabricator you like. You may also buy the board from PCBWay using this link (disclosure: I receive 10% of the sale value to go towards future PCB orders of my own):

(NOT YET LIVE)

<a href="https://www.pcbway.com/"><img src="https://www.pcbway.com/project/img/images/frompcbway-1220.png" alt="PCB from PCBWay" /></a>

## Required Equipment

- You will need basic tools, like a soldering iron, hot plate, and/or hot air rework station.
- You need a way to program the ROM chip(s). For NES games, I usually use the <a href="https://xgecu.myshopify.com/products/xgecu-new-t48-tl866-3gprogrammer-v12-01-support-28000-ics-for-spi-nor-nand-flash-emmc-bga153-162-169-100-221-tsop-sop-plcc">T48 programmer</a>.
- If you do not have an original CIC to transfer to this board, or a region unlock mod on your console, you will need an ATTINY13 with the <a href="http://forums.nesdev.com/download/file.php?id=5943">AVRCIC code by krikzz</a> to fake out the lockout chip. You will need a way to program these chips. I use the T48 to do so, but you can also use something like the <a href="https://www.microchip.com/en-us/development-tool/pg164130">PICkit 3.</a> Be sure to see <a href="https://github.com/MouseBiteLabs/NES-Cartridges/wiki/Programming-the-CIC">the tutorial on how to program these lockout chips,</a> as you need to change a few settings before programming the code.

## How to Program

<a href="https://github.com/MouseBiteLabs/NES-Cartridges/wiki/Preparing-the-ROM">Please check out the wiki pages on how to prepare the ROM and program the cartridge.</a>

## Board Configurations

This board is highly customizable. You *do not* need every single part on this board to make a game. The cartridge configuration you need for the game you want to make is mainly dependent on the mapping type. Depending on your needs, you only need to solder on certain components, which you can find below in the BOM section. You will also need to configure the game with the various solder jumpers on the back of the board.

<a href="https://github.com/MouseBiteLabs/NES-Cartridges/wiki/Discrete-Mapper">**I highly recommend checking out the various examples of board configurations on the wiki.**</a>

### Solder Jumpers

asdfadsfasdf

### Selecting U4

U4 is the main mapping chip for all mappers except NROM (which does not need one). U4B and U4C are 74'161 that have four sets of I/O, and U4A is the 74'377 which has eight. These I/O are connected to the data pins (D0-D7). If you're making a CNROM or UxROM game, you can use a 74'161 in the U4B socket; if you're making AxROM or BNROM, you can use a 74'161 in the U4C socket.

If you use the 74HCT377, you can achieve an "expanded" version of CNROM, UxROM, AxROM, and BNROM. This expanded memory has no functionality for games that do not use it - this feature is more for developers to take advantage of. One exception to this is Panesian games - these utilize the expanded CNROM mapper type, and therefore require the 74'377.

If you want an easy option to cover all your bases without having to think too hard about what chip to use, I recommend simply populating U4A (74HCT377).

### Special Mapper Types

There are a few special cases for a few obscure mapper types that this board supports:
- For making Panesian games, follow instructions for a CNROM board type, but you must use U4A.
- To achieve Mapper 180, follow instructions for a UxROM board type, but replace the 74'32 with a 74'08. See the BOM for more information.
- To achieve Mapper 87, follow instructions for a CNROM board type, but you must use U4A with pins 5 and 6 bent out to solder to the adjacent pins from the U4B footprint.
- To achieve Mapper 79 or 148, follow instructions for a CNROM board type, but you must use U4B with pin 11 bent inward under the part footprint to solder to the test point.

## Troubleshooting

<a href="https://github.com/MouseBiteLabs/NES-Cartridges/wiki/Troubleshooting-Tips">Please check out the wiki pages for troubleshooting tips.</a>

## Bill of Materials (BOM)

NOTE 1: The 39SF040 is listed as the recommended part for all of the following BOMs - it will cover any and all games, but you can also use the following chips if they are big enough for the game file you have:
- UV EPROM: 27C256, 27C512, 27C010, 27C020, 27C040, 27C080
- NOR Flash: 39SF512, 39SF010, 39SF020 

NOTE 2: The AS6C6264 is recommended for the CHR RAM for boards that require it, but the AS6C62256 also works.

All games will require the following parts:

| Reference | Value/Part Number | Package        | Description                     | Source                                           |
| --------- | ----------------- | -------------- | ------------------------------- | ------------------------------------------------ |
| U1 \*     | CIC / ATTINY13  | DIP-16 / DIP-8 | Region Lockout Chip             | [https://mou.sr/4h4SnUi](https://mou.sr/4h4SnUi) |
| U2        | 39SF040        | DIP-32         | PRG ROM                         | [https://mou.sr/47odNbz](https://mou.sr/47odNbz) |
| CC        | 22uF              | 5mm x 5mm      | Aluminum Electrolytic Capacitor | [https://mou.sr/4moiXKK](https://mou.sr/4moiXKK) |
| C1        | 0.1uF             | Radial, 5mm    | Capacitor (MLCC)                | [https://mou.sr/4mvAwIR](https://mou.sr/4mvAwIR) |
| C2        | 0.1uF             | Radial, 5mm    | Capacitor (MLCC)                | [https://mou.sr/4mvAwIR](https://mou.sr/4mvAwIR) |
| R8        | 100k              | Axial, 3.3mm   | Resistor                        | [https://mou.sr/3NOD0De](https://mou.sr/3NOD0De) |

\* This can be harvested from an original NES game (this is not needed if you have region modded your NES)

### NROM

These extra parts are required for NROM games:

| Reference | Value/Part Number | Package     | Description      | Source                                           |
| --------- | ----------------- | ----------- | ---------------- | ------------------------------------------------ |
| U3        | 39SF040           | DIP-32      | CHR ROM          | [https://mou.sr/47odNbz](https://mou.sr/47odNbz) |
| C3        | 0.1uF             | Radial, 5mm | Capacitor (MLCC) | [https://mou.sr/4mvAwIR](https://mou.sr/4mvAwIR) |

### UxROM

These extra parts are required for UNROM and UOROM games:

| Reference | Value/Part Number | Package     | Description      | Source                                           |
| --------- | ----------------- | ----------- | ---------------- | ------------------------------------------------ |
| U3        | AS6C6264          | DIP-28      | CHR RAM          | [https://mou.sr/3KQ1Tv5](https://mou.sr/3KQ1Tv5) |
| U4A \*    | 74HCT377          | DIP-20      | Octal Flip-Flop  | [https://mou.sr/4ozFyER](https://mou.sr/4ozFyER) |
| U4B \*    | 74HCT161          | DIP-16      | Binary Counter   | [https://mou.sr/4qlCT3n](https://mou.sr/4qlCT3n) |
| U5        | 74HCT32           | DIP-14      | Quad 2-in OR     | [https://mou.sr/471nOwi](https://mou.sr/471nOwi) |
| C3        | 0.1uF             | Radial, 5mm | Capacitor (MLCC) | [https://mou.sr/4mvAwIR](https://mou.sr/4mvAwIR) |
| C4A \*    | 0.1uF             | Radial, 5mm | Capacitor (MLCC) | [https://mou.sr/4mvAwIR](https://mou.sr/4mvAwIR) |
| C4B \*    | 0.1uF             | Radial, 5mm | Capacitor (MLCC) | [https://mou.sr/4mvAwIR](https://mou.sr/4mvAwIR) |
| C5        | 0.1uF             | Radial, 5mm | Capacitor (MLCC) | [https://mou.sr/4mvAwIR](https://mou.sr/4mvAwIR) |

\* Use either U4A/C4A *OR* U4B/C4B. Do not use both!

Special note: For Mapper 180, replace U5 with 74HCT08 ([https://mou.sr/3AM08eK](https://mou.sr/3AM08eK))

### CNROM

These extra parts are required for CNROM games:

| Reference | Value/Part Number | Package     | Description      | Source                                           |
| --------- | ----------------- | ----------- | ---------------- | ------------------------------------------------ |
| U3        | 39SF040           | DIP-32      | CHR ROM          | [https://mou.sr/47odNbz](https://mou.sr/47odNbz) |
| U4A \*    | 74HCT377          | DIP-20      | Octal Flip-Flop  | [https://mou.sr/4ozFyER](https://mou.sr/4ozFyER) |
| U4B \*    | 74HCT161          | DIP-16      | Binary Counter   | [https://mou.sr/4qlCT3n](https://mou.sr/4qlCT3n) |
| C3        | 0.1uF             | Radial, 5mm | Capacitor (MLCC) | [https://mou.sr/4mvAwIR](https://mou.sr/4mvAwIR) |
| C4A \*    | 0.1uF             | Radial, 5mm | Capacitor (MLCC) | [https://mou.sr/4mvAwIR](https://mou.sr/4mvAwIR) |
| C4B \*    | 0.1uF             | Radial, 5mm | Capacitor (MLCC) | [https://mou.sr/4mvAwIR](https://mou.sr/4mvAwIR) |

\* Use either U4A/C4A *OR* U4B/C4B. Do not use both!

Special note: Panesian and Mapper 87 games require U4A/C4A, Mapper 79 and 149 games require U4B/C4B.

### AxROM

These extra parts are required for AMROM, ANROM, AN1ROM, and AOROM games:

| Reference | Value/Part Number | Package     | Description      | Source                                           |
| --------- | ----------------- | ----------- | ---------------- | ------------------------------------------------ |
| U3        | AS6C6264          | DIP-28      | CHR RAM          | [https://mou.sr/3KQ1Tv5](https://mou.sr/3KQ1Tv5) |
| U4A \*    | 74HCT377          | DIP-20      | Octal Flip-Flop  | [https://mou.sr/4ozFyER](https://mou.sr/4ozFyER) |
| U4C \*    | 74HCT161          | DIP-16      | Binary Counter   | [https://mou.sr/4qlCT3n](https://mou.sr/4qlCT3n) |
| U6        | 74HCT02           | DIP-14      | Quad 2-in NOR    | [https://mou.sr/4qo4i4z](https://mou.sr/4qo4i4z) |
| C3        | 0.1uF             | Radial, 5mm | Capacitor (MLCC) | [https://mou.sr/4mvAwIR](https://mou.sr/4mvAwIR) |
| C4A \*    | 0.1uF             | Radial, 5mm | Capacitor (MLCC) | [https://mou.sr/4mvAwIR](https://mou.sr/4mvAwIR) |
| C4C \*    | 0.1uF             | Radial, 5mm | Capacitor (MLCC) | [https://mou.sr/4mvAwIR](https://mou.sr/4mvAwIR) |
| C6        | 0.1uF             | Radial, 5mm | Capacitor (MLCC) | [https://mou.sr/4mvAwIR](https://mou.sr/4mvAwIR) |

\* Use either U4A/C4A *OR* U4C/C4C. Do not use both!

### Color Dreams

These extra parts are required for Color Dreams games:

| Reference | Value/Part Number | Package     | Description      | Source                                           |
| --------- | ----------------- | ----------- | ---------------- | ------------------------------------------------ |
| U3        | 39SF040           | DIP-32      | CHR ROM          | [https://mou.sr/47odNbz](https://mou.sr/47odNbz) |
| U4A       | 74HCT377          | DIP-20      | Octal Flip-Flop  | [https://mou.sr/4ozFyER](https://mou.sr/4ozFyER) |
| C3        | 0.1uF             | Radial, 5mm | Capacitor (MLCC) | [https://mou.sr/4mvAwIR](https://mou.sr/4mvAwIR) |
| C4A       | 0.1uF             | Radial, 5mm | Capacitor (MLCC) | [https://mou.sr/4mvAwIR](https://mou.sr/4mvAwIR) |

### BNROM

These extra parts are required for BNROM games:

| Reference | Value/Part Number | Package     | Description      | Source                                           |
| --------- | ----------------- | ----------- | ---------------- | ------------------------------------------------ |
| U3        | AS6C6264          | DIP-28      | CHR RAM          | [https://mou.sr/3KQ1Tv5](https://mou.sr/3KQ1Tv5) |
| U4A \*    | 74HCT377          | DIP-20      | Octal Flip-Flop  | [https://mou.sr/4ozFyER](https://mou.sr/4ozFyER) |
| U4C \*    | 74HCT161          | DIP-16      | Binary Counter   | [https://mou.sr/4qlCT3n](https://mou.sr/4qlCT3n) |
| C3        | 0.1uF             | Radial, 5mm | Capacitor (MLCC) | [https://mou.sr/4mvAwIR](https://mou.sr/4mvAwIR) |
| C4A \*    | 0.1uF             | Radial, 5mm | Capacitor (MLCC) | [https://mou.sr/4mvAwIR](https://mou.sr/4mvAwIR) |
| C4C \*    | 0.1uF             | Radial, 5mm | Capacitor (MLCC) | [https://mou.sr/4mvAwIR](https://mou.sr/4mvAwIR) |

\* Use either U4A/C4A *OR* U4C/C4C. Do not use both!

### GNROM

These extra parts are required for GNROM games:

| Reference | Value/Part Number | Package     | Description      | Source                                           |
| --------- | ----------------- | ----------- | ---------------- | ------------------------------------------------ |
| U3        | 39SF040           | DIP-32      | CHR ROM          | [https://mou.sr/47odNbz](https://mou.sr/47odNbz) |
| U4A       | 74HCT377          | DIP-20      | Octal Flip-Flop  | [https://mou.sr/4ozFyER](https://mou.sr/4ozFyER) |
| C3        | 0.1uF             | Radial, 5mm | Capacitor (MLCC) | [https://mou.sr/4mvAwIR](https://mou.sr/4mvAwIR) |
| C4A       | 0.1uF             | Radial, 5mm | Capacitor (MLCC) | [https://mou.sr/4mvAwIR](https://mou.sr/4mvAwIR) |

## Revision History

### v1.1 - Release

- Added pad for using 28-pin PRG EPROMs.
- Fixed Mapper 079/148 instructions and added extra test point for proper configuration.

### v1.0 - Prototype

## Acknowledgements and Resources

- The <a href="https://www.nesdev.org/wiki/Nesdev_Wiki">Nesdev wiki</a> was *indispensible* for making this board, especially <a href="https://www.nesdev.org/wiki/User:Lidnariq/Discrete_Logic_Table">this specific page</a> by lidnariq.
- Continual thanks to all in the nesdev community for their resources, design tips, and support throughout the past half-decade.

## License

<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-sa/4.0/80x15.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>. You are able to copy and redistribute the material in any medium or format, as well as remix, transform, or build upon the material for any purpose (even commercial) - but you **must** give appropriate credit, provide a link to the license, and indicate if any changes were made.

©MouseBiteLabs 2025
