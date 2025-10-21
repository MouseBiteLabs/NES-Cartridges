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

## Troubleshooting

<a href="https://github.com/MouseBiteLabs/NES-Cartridges/wiki/Troubleshooting-Tips">Please check out the wiki pages for troubleshooting tips.</a>

## Bill of Materials (BOM)

The component groups required for the build you want to make are detailed above.

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
