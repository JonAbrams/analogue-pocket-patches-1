# analogue-pocket-patches

## How they're generated

To convert a ROM, all accesses to the [LCDC](https://gbdev.io/pandocs/LCDC.html) and [STAT](https://gbdev.io/pandocs/STAT.html) registers need to be bit reversed. The pocket format also moves the LCDC hardware register to offset 0xFF4E from 0xFF40 in the actual Game Boy hardware. To make it work, you need to go through all of the code in the ROM and replace every instance where these registers are used (and memory locations that have values that get transferred to/from these registers) with the bit reversed operation (i.e. $83 -> $C1) and replace every LCDC usage with the new address ($4e or $ff4e).

For my workflow, to generate the `.pocket` file, the ROM is first decompiled with [mgbdis](https://github.com/mattcurrie/mgbdis) and then recompiled with [rgbds](https://github.com/gbdev/rgbds) after patching the above issues and whatever else pops up. Once it's recompiled, the [header](https://gbdev.io/pandocs/The_Cartridge_Header.html#0104-0133---nintendo-logo) needs to be modified to use Analogue's header rather than the Nintendo header.

I then generate the final IPS patch using [lipx](https://github.com/kylon/Lipx), which compares the original ROM with the patched version.

To debug issues with the patches, I have provided a copy of SameBoy that is patched to run `.pocket` files and to print some warnings if there are register accesses to 0xFF40. It is available here: [https://github.com/JoseJX/SameBoy](https://github.com/JoseJX/SameBoy).

Hopefully this helps!

## How to use the patches

You will need IPS patching software, the IPS patch for your chosen game and the specific ROM revision for the patch. Once the IPS patch is applied you need to change the file extension from `.gb` to `.pocket` and place them in a `GB Studio` folder on the root of your microSD card. Please make sure to keep the filename short, longer filenames appear to cause trouble.

Please note that link cable functionality and the real-time clock are not supported in GB Studio mode.

## Table of Contents

Game | System 
--- | --- 
[The Adventures of Star Saver](#the-adventures-of-star-saver) | GB
[Alleyway](#alleyway) | GB
[Balloon Kid](#balloon-kid) | GB
[Bart Simpson's Escape from Camp Deadly](#bart-simpsons-escape-from-camp-deadly) | GB
[Batman - The Video Game](#batman---the-video-game) | GB
[Bionic Commando](#bionic-commando) | GB
[Blades of Steel](#blades-of-steel) | GB
[Bubble Bobble](#bubble-bobble) | GB
[Castlevania - The Adventure](#castlevania---the-adventure) | GB
[Castlevania Legends](#castlevania-legends) | GB
[Castlevania II - Belmont's Revenge](#castlevania-ii---belmonts-revenge) | GB
[Catrap](#catrap) | GB
[Commander Keen](#commander-keen) | GBC
[Duck Tales](#duck-tales) | GB
[Duck Tales 2](#duck-tales-2) | GB
[Final Fantasy Legend](#final-fantasy-legend) | GB
[Final Fantasy Legend II](#final-fantasy-legend-ii) | GB
[Final Fantasy Legend III](#final-fantasy-legend-iii) | GB
[Game & Watch Gallery](#game--watch-gallery) | GB
[Game & Watch Gallery 2](#game--watch-gallery-2) | GBC
[Gear Works](#gear-works) | GB
[INFGMB - Infocom Z3 Interpreter](#infgmb) | GBC
[Kid Dracula](#kid-dracula) | GB
[Kid Icarus - Of Myths and Monsters](#kid-icarus---of-myths-and-monsters) | GB
[Kirby's Block Ball](#kirbys-block-ball) | GB
[Kirby's Dream Land](#kirbys-dream-land) | GB
[Kirby's Dream Land 2](#kirbys-dream-land-2) | GB
[Kirby's Pinball Land](#kirbys-pinball-land) | GB
[Kirby's Star Stacker](#kirbys-star-stacker) | GB
[Marble Madness](#marble-madness) | GB
[Marble Madness (GBC)](#marble-madness-color) | GBC
[Mario's Picross](#marios-picross) | GB
[Mega Man - Dr. Wily's Revenge](#mega-man---dr-wilys-revenge) | GB
[Mega Man II](#mega-man-ii) | GB
[Mega Man III](#mega-man-iii) | GB
[Mega Man IV](#mega-man-iv) | GB
[Mega Man V](#mega-man-v) | GB
[Metal Gear Solid](#metal-gear-solid) | GBC
[Mole Mania](#mole-mania) | GB
[Motocross Maniacs 2](#motocross-maniacs-2) | GBC
[Mr. Driller](#mr-driller) | GBC
[Ms. Pac-Man](#ms-pac-man) | GB
[Pokemon Puzzle Challenge](#pokemon-puzzle-challenge) | GBC
[Popeye 2](#popeye-2) | GB
[QIX](#qix) | GB
[Revenge of the 'Gator](#revenge-of-the--gator) | GB
[Side Pocket](#side-pocket) | GB
[Solar Striker](#solar-striker) | GB
[Super Off Road](#super-off-road) | GB
[Super R.C. Pro-Am](#super-rc-pro-am) | GB
[Teenage Mutant Ninja Turtles - Fall of the Foot Clan](#teenage-mutant-ninja-turtles---fall-of-the-foot-clan) | GB
[Teenage Mutant Ninja Turtles II - Back From the Sewers](#teenage-mutant-ninja-turtles-ii---back-from-the-sewers) | GB
[Tetris 2](#tetris-2) | GB
[Tetris Attack](#tetris-attack) | GB
[Tetris Blast](#tetris-blast) | GB
[Trax](#trax) | GB
[Wordtris](#wordtris) | GB
[Yoshi](#yoshi) | GB
[Yoshi's Cookie](#yoshis-cookie) | GB

## The Adventures of Star Saver

This patch converts `The Adventures of Star Saver (U,E)` to the `.pocket` format.

ROM MD5: `91ecec5f8d06f18724bd1462b53c4b3d`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/StarSaver.ips).

## Alleyway

This patch converts `Alleyway (W)` to the `.pocket` format.

This was updated to fix an error on boot. (2021/12/31)

ROM MD5: `91128778a332495f77699eaf3a37fe30`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/Alleyway.ips).

## Balloon Kid

This patch converts `Balloon Kid (U,E)` to the `.pocket` format.

ROM MD5: `f70c60ca87714fa9d81be60c9ac93de0`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/BalloonKid.ips).

## Bart Simpson's Escape from Camp Deadly

This patch converts `Bart Simpson's Escape from Camp Deadly (U,E)` to the `.pocket` format.

ROM MD5: `e731fa23d9cd0c3d4dec7d5565beef61`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/CampDeadly.ips).

## Batman - The Video Game

This patch converts `Batman - The Video Game (U,E)` to the `.pocket` format.

ROM MD5: `03c6d84a951be6703b7458478f4277b9`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/Batman.ips).

## Bionic Commando

This patch converts `Bionic Commando (U)` to the `.pocket` format.

ROM MD5: `f89a33de3fa660a13ec29bb323efffa9`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/BionicCommando.ips).

## Blades of Steel

This patch converts `Blades of Steel (U)` to the `.pocket` format.

NOTE: After selecting a menu option, press the buttons a bunch, it seems to get stuck waiting, but it happens on the original cart too.

ROM MD5: `302caa3ceddccc5fba36787b44d25da7`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/BladesOfSteel.ips).

## Bubble Bobble

This patch converts `Bubble Bobble (U,E)` to the `.pocket` format.

ROM MD5: `11c49d405eef2174d9c14682204bb458`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/BubbleBobble.ips).

## Castlevania - The Adventure

This patch converts `Castlevania - The Adventure (U)` to the `.pocket` format.

ROM MD5: `0b4410c6b94d6359dba5609ae9a32909`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/CastlevaniaAdventure.ips).

## Castlevania II - Belmont's Revenge

This patch converts `Castlevania II - Belmont's Revenge (U)` to the `.pocket` format.

ROM MD5: `7c65e9da405d2225d079f75e56276822`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/Castlevania2.ips).

## Castlevania Legends

This patch converts `Castlevania Legends (U)` to the `.pocket` format.

ROM MD5: `1475824e7262c0d6359f43c287e034a5`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/CastlevaniaLegends.ips).

## Catrap

This patch converts `Catrap (U)` to the `.pocket` format.

ROM MD5: `5a75fe8de54e4cbd09cae23f050f6965`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/Catrap.ips).

## Commander Keen

This patch converts `Commander Keen (U,E)` to the `.pocket` format.

ROM MD5: `94d2aa3fbda301f9c0d0c16e00743183`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/CommanderKeen.ips).

## Duck Tales

This patch converts `Duck Tales (U)` to the `.pocket` format.

ROM MD5: `785441d3d75913393807b10b3194dc48`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/DuckTales.ips).

## Duck Tales 2

This patch converts `Duck Tales 2 (U)` to the `.pocket` format.

ROM MD5: `b4e5876c5acedd12b62e25a12973a4ae`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/DuckTales2.ips).

## Final Fantasy Legend

This patch converts `Final Fantasy Legend (U)` to the `.pocket` format.

ROM MD5: `d5c27ff8cb1b69cb56df4ff170e2baf0`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/FFL1.ips).

## Final Fantasy Legend II

This patch converts `Final Fantasy Legend II (U)` to the `.pocket` format.

ROM MD5: `2bb0df1b672253aaa5f9caf9aab78224`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/FFL2.ips).

## Final Fantasy Legend III

This patch converts `Final Fantasy Legend III (U)` to the `.pocket` format.

ROM MD5: `db156bc96b528996ce1bf771195171af`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/FFL3.ips).

## Game & Watch Gallery
This patch converts `Game & Watch Gallery (U)` to the `.pocket` format.

ROM MD5: `d5081250257e0dafcb8fe8720fcb9f28`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/GnW1.ips).

## Game & Watch Gallery 2

This patch converts `Game & Watch Gallery 2 (U,E)` to the `.pocket` format.

ROM MD5: `cbf4a5b2ff566554b014118e3d0e3e9a`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/GnW2.ips).

## Gear Works

This patch converts `Gear Works (U,E)` to the `.pocket` format.

ROM MD5: `16af858484041d572299b501ead2b788`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/GearWorks.ips).

## INFGMB

[INFGMB](https://problemkaputt.de/infgmb.htm) is an Infocom Z-Machine interpreter for the Game Boy.

This patch is a bit different. To successfully use this patch, you will need to apply the IPS to the ROM linked above and then append your Z3 or lower Z-Machine game to the end of the patched ROM.

In Linux or OSX, this command is something like: `cat infgmb.pocket game.z3 > game.pocket`

In Windows (and DOS I guess), you're best served doing it from the terminal too. Change into the directory where the patched `.gbc` file and game file are located and type: `copy /B infgmb.pocket + game.z3 game.pocket`.

Copy the resulting `game.pocket` file to your SD card. Repeat this process for each Z-Machine game you'd like to play.

ROM MD5: `65a5a0cb3c339ec473053c64c2218ab9`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/INFGMB.ips).

## Kirby's Block Ball

This patch converts `Kirby's Block Ball (U,E)` to the `.pocket` format.

ROM MD5: `203db7ddc72359e4db5e9ab42a6f0ba8`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/KirbysBlockBall.ips).

## Kirby's Dream Land

This patch converts `Kirby's Dream Land (U,E)` to the `.pocket` format.

This patch was updated to fix [bug #4](https://github.com/JoseJX/analogue-pocket-patches/issues/4) - (2021/12/30)

ROM MD5: `a66e4918edcd042ec171a57fe3ce36c3`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/KirbysDream.ips).

## Kirby's Dream Land 2

This patch converts `Kirby's Dream Land 2 (U,E)` to the `.pocket` format.

ROM MD5: `ddb5bfae32b0ca39cf8ab6c46880126c`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/KirbysDream2.ips).

## Kirby's Pinball Land

This patch converts `Kirby's Pinball Land (U,E)` to the `.pocket` format.

ROM MD5: `f711ed10307d4ea27223fe965595b123`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/KirbysPinball.ips).

## Kirby's Star Stacker

This patch converts `Kirby's Star Stacker (U,E)` to the `.pocket` format.

ROM MD5: `f4c0bf35939be6786c099e9eb4635919`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/KirbyStarStack.ips).

## Kid Dracula

This patch converts `Kid Dracula (U,E)` to the `.pocket` format.

ROM MD5: `24a6b4457a511cc667e9ac25417401ab`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/KidDracula.ips).

## Kid Icarus - Of Myths and Monsters

This patch converts `Kid Icarus - Of Myths and Monsters (U,E)` to the `.pocket` format.

ROM MD5: `23c7be98ac9a4d3b046ad1be3f0965e4`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/KidIcarus.ips).

## Marble Madness

This patch converts `Marble Madness (U,E)` to the `.pocket` format.

ROM MD5: `f489b8eb7dc88a39842f20a7f7165e5b`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/MarbleMadness.ips).

## Marble Madness (Color)

This patch converts `Marble Madness (GBC) (U,E)` to the `.pocket` format.

ROM MD5: `d2711ff066f40c4e6c471b79da0f08b7`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/MarbleMadnessColor.ips).

## Mario's Picross

This patch converts `Mario's Picross (U,E)` to the `.pocket` format.

ROM MD5: `ccaf9331318d4dfe3d1ee681928a74fd`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/MarioPicross.ips).

## Mega Man - Dr. Wily's Revenge

This patch converts `Mega Man - Dr. Wily's Revenge (U)` to the `.pocket` format.

ROM MD5: `4ba4398181d98958fa7434ba7716f11a`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/MegaMan1.ips).

## Mega Man II

This patch converts `Mega Man II (U)` to the `.pocket` format.

ROM MD5: `7fe07271d04ed9e0bc0663dde55a2ae4`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/MegaMan2.ips).

## Mega Man III

This patch converts `Mega Man III (U)` to the `.pocket` format.

ROM MD5: `4c614f884a07872f12056ad1a421e1f9`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/MegaMan3.ips).

## Mega Man IV

This patch converts `Mega Man IV (U)` to the `.pocket` format.

It has been updated to fix [bug #3](https://github.com/JoseJX/analogue-pocket-patches/issues/3).

ROM MD5: `8a00f627b8902c92327435901c249e19`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/MegaMan4.ips).

## Mega Man V

This patch converts `Mega Man V (U)` to the `.pocket` format.

Updated to address [bug #8](https://github.com/JoseJX/analogue-pocket-patches/issues/8) (2022/01/04)

ROM MD5: `ceb17d831b410d91aa41bf2819cbed82`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/MegaMan5.ips).

## Metal Gear Solid

This patch converts `Metal Gear Solid (U)` to the `.pocket` format.

ROM MD5: `f6dd1b1e5747412b9e5f25376c972d5a`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/MetalGear.ips).

## Mole Mania

This patch converts `Mole Mania (U)` to the `.pocket` format.

It has been updated to fix [bug #2](https://github.com/JoseJX/analogue-pocket-patches/issues/2).

It has been updated again for another missed register access. (2021/12/30)

ROM MD5: `f28ade3926852a8ad2e449c274683956`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/MoleMania.ips).

## Motocross Maniacs 2

This patch converts `Motocross Maniacs 2 (U)` to the `.pocket` format.

This patch was updated to fix a missing conversion. (2021/12/31)

ROM MD5: `4d08e5553356aecd728b5ef7d78ee261`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/Motocross2.ips).

## Mr. Driller

This patch converts `Mr. Driller (U)` to the `.pocket` format.

ROM MD5: `76fa4014bfbb0ee2b63267af7ac373f2`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/MrDriller.ips).


## Ms. Pac-Man

This patch converts `Ms. Pac-Man (U)` to the `.pocket` format.

ROM MD5: `ffa8642a18781fbe79df436a761a9775`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/MsPacMan.ips).

## Revenge of the 'Gator
This patch converts `Revenge of the 'Gator (U,E)` to the `.pocket` format.

ROM MD5: `113d8f894df6b8c3641b2ba1fe60c250`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/Gator.ips).

## Pokemon Puzzle Challenge

This patch converts `Pokemon Puzzle Challenge (U)` to the `.pocket` format.

ROM MD5: `f9ec4cc3c9df3887dc731ccf53663ffb`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/PokePuzzle.ips).

## Popeye 2

This patch converts `Popeye 2 (U)` to the `.pocket` format.

ROM MD5: `30b579d82ae755bd37c1d4157a96129c`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/Popeye2.ips).

## QIX

This patch converts `QIX (W)` to the `.pocket` format.

ROM MD5: `1c94dccdfaaa0c3e1d6bda5969704885`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/QIX.ips).

## Side Pocket

This patch converts `Side Pocket (U)` to the `.pocket` format.

ROM MD5: `3dbe9be772ca50da3a76d8860c7b08e2`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/SidePocket.ips).

## Solar Striker

This patch converts `Solar Striker (W)` to the `.pocket` format.

ROM MD5: `83bed4ebefeece45748258fd2ef105b3`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/SolarStriker.ips).

## Super Off Road

This patch converts `Super Off Road (U)` to the `.pocket` format.

ROM MD5: `85d05f95c07ed1b7d787062fe4d2e251`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/SuperOffRoad.ips).

## Super R.C. Pro-Am

This patch converts `Super R.C. Pro-Am (U,E)` to the `.pocket` format.

ROM MD5: `9ba2999ef3ecf9e27ac6c88e995c9d7a`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/SuperRC.ips).

## Teenage Mutant Ninja Turtles - Fall of the Foot Clan

This patch converts `Teenage Mutant Ninja Turtles - Fall of the Foot Clan (U)` to the `.pocket` format.

ROM MD5: `ad868e84fb6071a3b6a211d16e6cbb66`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/TMNT1.ips).

## Teenage Mutant Ninja Turtles II - Back From the Sewers

This patch converts `Teenage Mutant Ninja Turtles II - Back From the Sewers (U)` to the `.pocket` format.

ROM MD5: `0221de99d11f50f79430c8ff9b430994`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/TMNT2.ips).

## Tetris 2

This patch converts `Tetris 2 (U,E)` to the `.pocket` format.

ROM MD5: `0a2e27e279ee4faac326b0cf620b269b`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/Tetris2.ips).

## Tetris Attack

This patch converts `Tetris Attack (U) (1.0)` to the `.pocket` format.

ROM MD5: `7fbda0c87af7701bb5e75c2a77bb0143`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/TetrisAttack.ips).

## Tetris Blast
This patch converts `Tetris Blast (U,E)` to the `.pocket` format.

ROM MD5: `0affc9df2e1220ea4573deb6cb2d4b32`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/TetrisBlast.ips).

## Trax

This patch converts `Trax (U,E)` to the `.pocket` format.

ROM MD5: `89ecf5b28d5cc84208cfc39dc2d96598`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/Trax.ips).

## Wordtris

This patch converts `Wordtris (U)` to the `.pocket` format.

ROM MD5: `29c71c474c2fa00eeac79ddb55c2c174`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/Wordtris.ips).

## Yoshi

This patch converts `Yoshi (U)` to the `.pocket` format.

ROM MD5: `a8804c8514619cc918960c2008ed65d1`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/Yoshi.ips).

## Yoshi's Cookie

This patch converts `Yoshi's Cookie (U)` to the `.pocket` format.

ROM MD5: `bc1a3848092bdc900c157996c29a7783`

You can [download the Analogue Pocket IPS patch here](https://github.com/JoseJX/analogue-pocket-patches/blob/main/YoshisCookie.ips).

