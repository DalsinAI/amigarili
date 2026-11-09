Ri-li 3.1.6 for AmigaOS 3.x
===========================

Ri-li (Dominique Roux-Serret; now kept by Johnny Jazeix,
https://github.com/petitlapin/Li-Ri), the arcade game with a wooden toy
train: steer the engine round the track, pick up the wagons and don't hit
your own tail. For AmigaOS 3.x on a 68040 or 68060 with an FPU and an RTG
screen, on OpenGPU's SDL 2.

Base: ri-li_3.1.6.orig.tar.gz from Debian (upstream's GitHub tag v3.1.6,
sha256 c1edff0ec4b5d2afddefb12350d6a6e9779888354edfae4fd3073fad86e80bb3).
Branch team2/rili-amiga.

Status: plays in the lab (Instance-45 on GFOpenUp 0.8.19, 6 November
2026): full screen (its default) at the Workbench's size, the language
picker, the menu, a Normal game on level 1 (the train running and turning,
the wagons picked up, the score), the pause menu, Exit Game to the high
scores, and Quit back to the Shell; li-ri.ini written. The music (MOD and
XM, through SDL2_mixer.module) and the sounds load without an error; the
lab's sound is muted, so not heard.


What you need
-------------

- A 68040 or 68060 with an FPU, AmigaOS 3.x, an RTG card (or the
  AmigaChrome lab).
- GFOpenUp 0.8.18 or later: LIBS:OpenGPU/SDL2.module and SDL2_mixer.module.
- About 140 MB of disk (each of the 19 languages has its own pictures).


How to play
-----------

Open the Ri-li icon, or run Ri-li from a Shell. The game reads its data
from the drawer's data/ and keeps its settings and high scores in li-ri.ini
beside the program.



Standard keys
-------------

Every AmiCradle game has the same keys on Right Amiga (GFOpenUp's
SDL2.module, after 0.8.26):

- Right Amiga + F: window or full screen, remembered for next time
- Right Amiga + P: pause (Right Amiga + P again goes on)
- Right Amiga + Q: quit
- Right Amiga + M: free the mouse pointer, or let the game take it again
- Right Amiga + S: a screenshot in the drawer's Screenshots
- Help: this game's keys (the drawer's Controls file)
- Right Amiga + F1, F2: F11, F12; Right Amiga + cursor keys: Page Up,
  Page Down, Home, End

The FULLSCREEN tooltype on the game's icon (take the brackets off) starts
it full screen.


Building
--------

    make -f amiga/Makefile.amigaos -j2 dist

with GFOpenAmigaGCC 16.2.0-open4 and the OpenGPU kit (see the Makefile's
head). The drawer is dist/Ri-li (and dist/Ri-li.info).


What was changed
----------------

- src/utils.cc: the data in PROGDIR:data (upstream's AmigaOS 4 branch of
  GetPath, which named PROGDIR:, now serves AmigaOS 3 too) and the
  settings in PROGDIR: (SDL_GetPrefPath has no home folder here).
- amiga/amiga_prelude.hpp (included before every file): std::stoi and the
  other C99 calls the GCC 16 stove's libstdc++ for the 68040 leaves out.
- amiga/simpleini: SimpleIni v4.22 (MIT), which upstream's CMake fetches.
- amiga/stack.c: 512 KB of stack.


Licences
--------

Ri-li: GPL 2 or GPL 3 (COPYING.txt has the GPL 3). Its music (jeu1.xm,
jeu2.xm, menu.mod): GPL 3, Maf464 (COPYING-Music.txt). SimpleIni: MIT
(SimpleIni-LICENCE.txt). The Amiga files (amiga/): GPL 2 or later, the
AmiCradle Team.
