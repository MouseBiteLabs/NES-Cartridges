# Nintendo Entertainment System (NES) Discrete Mapper Cartridge

This is an updated design of my old <a href="https://mousebitelabs.com/2020/09/11/nes-reproduction-quick-guide-custom-pcb/">NES Discrete cartridge boards</a>. Functionally, this design is nearly the same as the older one, but I added compatibility for a few new mappers and expanded the available memory for some mapper types, and under the hood I have ported the project over from Eagle to KiCad and heavily cleaned up the schematic and some of the trace routings. This version is also fully open source!

[pics]

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
