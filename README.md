# "Erasoft" & "RQ progs" games, intros, etc.

A selection of my Commodore games, intros, trainers and recracks from '88 to '92 (for NTSC, although they might work on PAL as well)

_(The story behind the preservation of these games: https://retro.moe/2016/06/06/the-quest-for-the-sacred-diskettes/ )_

# Games
In chronological order:

## Race

![](https://lh3.googleusercontent.com/-vXoL08QA8NA/V0karcOjG5I/AAAAAAABeF8/aObHvpmedjsJ6DBrDRlEpG8wPkfX_UdJQCCo/s400/Screen%2BShot%2B2016-05-28%2Bat%2B1.10.40%2BAM.png)
![](https://lh3.googleusercontent.com/-zm2sCXWTkhY/V0kar3dAGVI/AAAAAAABeGE/0bTI-pWgHYoZrvGW6F100lM7Z9ofaYv-wCCo/s400/Screen%2BShot%2B2016-05-28%2Bat%2B1.10.49%2BAM.png)
![](https://lh3.googleusercontent.com/-NnTJzJPwPY0/V0karhaFMyI/AAAAAAABeGA/G-u2MmwtWE46u5BKDb80Q3CKzGTyduKEQCCo/s400/Screen%2BShot%2B2016-05-28%2Bat%2B1.11.54%2BAM.png)

* Download: [race.d71](../../raw/master/disks/race.d71)
* Platform: C128
* Year: 1990
* About: Simple "racing" single-player game
* Credits: self
* Instructions:
    * Use joystick in port #2 to play (up-down movements).
    * There are 8 levels and you have to complete two laps for each level


## Teenage Mutant Runner Turtle

![](https://lh3.googleusercontent.com/-hF7vk5UWFck/V0kcow9Bw_I/AAAAAAABeGQ/JMMdaL60pbwIPm0jQ2K1nb2V6FrNWBN4QCCo/s400/Screen%2BShot%2B2016-05-28%2Bat%2B1.14.30%2BAM.png)
![](https://lh3.googleusercontent.com/-YF2-LGLll-I/V0kcpHq30qI/AAAAAAABeGU/9lEwqD5kQJIaavHzjgsf75nxFwjQhRYWwCCo/s400/Screen%2BShot%2B2016-05-28%2Bat%2B1.15.13%2BAM.png)
![](https://lh3.googleusercontent.com/-e6VavywLkJU/V0kcpISdRwI/AAAAAAABeGY/xkmZDlpdPkM7p8dcDMp4IONOOoIh8ymHQCCo/s400/Screen%2BShot%2B2016-05-28%2Bat%2B1.20.06%2BAM.png)

* Download: [tmrt.d71](../../raw/master/disks/tmrt.d71)
* Year: 1991
* About: A single-player rescue-your-girlfriend game
* Credits: self, except:
    * music was ripped from somewhere
    * clouds were ripped from BC's Quest for Tire
* Instructions:
    * Rescue your girlfriend.
    * Use joystick in port #2 to play.
    * Mechanics borrowed from BC's Quest for Tire.
    * There are 3 levels.
    * When you complete a level, `lives = lives + 1`. But you cannot have more than 5 lives

## Puncher

![](https://lh3.googleusercontent.com/-SDlgEXXgK4I/V0kdLaqwxNI/AAAAAAABeGg/msVD7m2KoOAUb_fvYjoePIWF7qnLwsoCwCCo/s400/Screen%2BShot%2B2016-05-28%2Bat%2B1.22.34%2BAM.png)
![](https://lh3.googleusercontent.com/-7OjU8-yQ7o4/V0kdLYY8KJI/AAAAAAABeGk/LUSHD7Efd9of2JufbJUtyzAProGrhItwgCCo/s400/Screen%2BShot%2B2016-05-28%2Bat%2B1.22.40%2BAM.png)
![](https://lh3.googleusercontent.com/-Xuc6NxhlnL8/V0kdLZs1ufI/AAAAAAABeGc/_QPERAAoBsUr3j_F1fSp_lssdoVi-Jv2QCCo/s400/Screen%2BShot%2B2016-05-28%2Bat%2B1.22.46%2BAM.png)

* Download: [puncher.d71](../../raw/master/disks/puncher.d71)
* Platform: C128
* Year: 1992
* Credits: self
* Instructions (original notes in spanish: [puncher.pdf](../../raw/master/scans/puncher.pdf))
    * You don't really play in this game.
    * You need to program your boxer using assembly language.
    * Kind of 'Core Wars' but much much much simpler
    * Reach 10000 points in order to win
    * The game has a kind of anti-cheat mechanism that can be easily bypassed
    * Files:
        * "AAAA": Erasoft intro at `$1300`
        * "AAAB": Left player at `$2000`. See below for details
        * "AAAC": Right player at `$2400`. See below for details
        * "AAAD": Font at `$3000`
        * "AAAE": Anti-cheat code loaded at `$1c01`. Main at `$1c10`, called from `$1776`
        * "AAAF": Game documentation loaded at `$3000`
        * "AAAG": Game logic code loaded `$1300`. See below for details
    * File "AAAG" (game logic):
        * `$1300`: Init players
        * `$1400`: Left player dispatcher
        * `$1403`: Left player joystick #2 input
        * `$14b0`: Left player "main logi handler" code
        * `$1500`: Right player dispatcher
        * `$1503`: Right player joystick #1 input
        * `$15b0`: Right player "main logic handler" code
        * `$1600`: Points handler code
        * `$1618`: Points for left player
        * `$1688`: Points for right player
        * `$1700`: Game Over message
        * `$174d`: IRQ entry point
        * `$17ff`: Copy of `$d01e` (sprite-to-sprite collision detection)
        * `$1800`: Validate players
    * File "AAAB" (left player logic):
        * Logic code:
            * it just hits the opponent when distances is less than 48 pixels (expanded sprite length)
            * it also disables joystick movment while hitting. cheats!
            * cheating can be detected by game logic while C= key is pressed
        * `$2000 - $217f`: Data for 6 sprites: head, body, legs #1, legs #2, punch hi, punch low
        * `$2180, $2181`: Higher punch, lower punch power. Must comply with: `$2180 + $2181 == 255`
        * `$2182, $2183`: Higher defense, lower defense. Must comply with: `$2182 + $2183 == 255`
        * `$2184 - $2193`: Player name
        * `$2194`: Player logic
        * Uses sprites #0 (head), #1 (body), #2 (legs) and #3 (arm)
        * Dispatch code at `$1400` (in file "AAAG")
        * Player code can jump to `$1403` to handle joystick movement, otherwise to `$14b0`
    * File "AAAC" (right player logic)
        * Logic code: it just flips the sprites horizontally every N seconds
        * `$2400 - $257f`: Data for 6 sprites: head, body, legs #1, legs #2, punch hi, punch low
        * `$2580, $2581`: Higher punch, lower punch power. Must comply with: `$2580 + $2581 == 255`
        * `$2582, $2583`: Higher defense, lower defense. Must comply with: `$2582 + $2583 == 255`
        * `$2584 - $2593`: Player name
        * `$2594`: Player logic
        * Uses sprites #4 (head), #5 (body), #6 (legs), and #7 (arm)
        * Dispatch code at `$1500` (in file "AAAG")
        * Player code can jump to `$1503` to handle joystick movement, otherwise to `$15b0`

## Chardef v2.32

![](https://lh3.googleusercontent.com/-YbCdeAmihKE/V0kegmvPk5I/AAAAAAABeG4/7h81q7xJLVMbjtDYPw84_bmgLjsBExLiACCo/s400/Screen%2BShot%2B2016-05-28%2Bat%2B1.24.30%2BAM.png)
![](https://lh3.googleusercontent.com/-LiSX52KJ-Ig/V0kegkZtp2I/AAAAAAABeGw/Fn9QU0VXlxwqav8afiqe50eet1FC1wECACCo/s400/Screen%2BShot%2B2016-05-28%2Bat%2B1.27.53%2BAM.png)
![](https://lh3.googleusercontent.com/-R1Xm6o4I5Wc/V0kegsPeFkI/AAAAAAABeG0/OqpzwENEsWEKf-Sr3MoUAx5mKtTLi5WUQCCo/s400/Screen%2BShot%2B2016-05-28%2Bat%2B1.28.15%2BAM.png)

* Download: [chardef_232.d71](../../raw/master/disks/chardef_232.d71)
* Platform: C128
* Year: 1992
* About: A character editor, the grand-daddy of [VChar64](https://github.com/ricardoquesada/vchar64)
* Credits: self
* Instructions (original notes in spanish: [chardef.pdf](../../raw/master/scans/chardef.pdf))
    * This is a "Terminate-And-Stay-Resident" program. While resident, you can do whatever you want, like saving the charset to disk using `BSAVE`.
    * F1: Save changes made in the char editor
    * F2: Save Screen RAM to `$3000`
    * F3: Rotate clock-wise
    * F4: Flip Horizontally
    * F5: Invert
    * F6: Clean
    * F7: Load the selected char in the editor
    * F8: Load Screen RAM from `$3000`
    * Joy 2: Up,Down,Left,Right: Scroll the editor data
    * Joy 2: Button + Up, Button + Down: Move the split screen up or down
    * Alt or Joy 1 Up: Display the editor frame
    * Shift + Alt: Reset charset
    + Shift + C=: switch between charset 1 and charset 2

## The Race

![](https://lh3.googleusercontent.com/-svXju9Jx7rw/V0kfaPWJdAI/AAAAAAABeHE/bTYuRR65kGsX70xw6AISBzCIw86cHmvywCCo/s400/Screen%2BShot%2B2016-05-28%2Bat%2B1.30.35%2BAM.png)
![](https://lh3.googleusercontent.com/-2yn1FPlbTIw/V0kfaEcw3rI/AAAAAAABeHA/qVQ1QRF42Fo7rjoQ6h4N0wctzOBO0JTQQCCo/s400/Screen%2BShot%2B2016-05-28%2Bat%2B1.31.19%2BAM.png)
![](https://lh3.googleusercontent.com/-UKQUiz7j5as/V0kfZ57r3iI/AAAAAAABeHI/yMPZuELXOaIZnAeS40NP0aqmSayQ25KcwCCo/s400/Screen%2BShot%2B2016-05-28%2Bat%2B1.31.33%2BAM.png)

* Download: [therace.d71](../../raw/master/disks/therace.d71)
* Platform: C128
* Year: 1992
* About: A two-player split-screen horizontal racing game
* Credits: self
* Instructions:
    * Player one (top) use Joy #2
    * Player two (bottom) use Joy #1
    * Joy Up / Down: Move the player up / down
    * Joy Up / Down + Button: Faster up / down movement
    * Joy Left / Right: Accelerate / decelerate
    * The player with the __lowest__ score is the one that wins
    * Collision: points = points + 5
* Bugs:
    * Use "True Drive Emulation" in VICE to prevent a race condition. Otherwise the intro screen won't display correctly

# Intros

I also coded some intros. The better looking ones are these two intros:

## Intro 10 (NTSC only)

![Intro 10](https://lh3.googleusercontent.com/-fOIeZv2pj1E/V1MP5ZrMuTI/AAAAAAABeRg/LYkVmkKovtAkBOX8mLfMLjN_ADiNcyicgCCo/s400/Screen%2BShot%2B2016-06-04%2Bat%2B2.25.07%2BPM.png)

* Download: [intro 10 NTSC ONLY.d64](../../raw/master/disks/intro_10_NTSC_ONLY.d64)
* Platform: C64

## Intro 15

![Intro 15](https://lh3.googleusercontent.com/-0oABlr-9GGE/V1MVJhnY3XI/AAAAAAABeRo/Cd10LKLaRRgmdqmHyXiOpHI3iWvE0JPoQCCo/s400/Screen%2BShot%2B2016-06-04%2Bat%2B2.51.00%2BPM.png)

* Download: Included in [The Race.71](../../raw/master/disks/therace.d71)
* Platform: C128

# Trainers

I did some trainers as well for C64 games, like:

![Giana Sisters](https://lh3.googleusercontent.com/-sAGP9B42SDw/V1TMAMnhnvI/AAAAAAABeVE/FIKqjsO5PE4kcV3LzSnxQXLet9stoHG9wCCo/s144/Screen%2BShot%2B2016-06-05%2Bat%2B9.50.16%2BPM.png)![Galaxy](https://lh3.googleusercontent.com/-l4EZga5QkcI/V1TL_675mdI/AAAAAAABeU8/d1soq5XLQX4ujUIuzUfYq8rSStC0YqWIwCCo/s144/Screen%2BShot%2B2016-06-05%2Bat%2B10.00.40%2BPM.png)![Hard Hat Mack](https://lh3.googleusercontent.com/-cQgExE6Ar2I/V1TMACZlB7I/AAAAAAABeVA/hKAdIOFUydAU0OgNP3EEU2j-a0St9ih0wCCo/s144/Screen%2BShot%2B2016-06-05%2Bat%2B9.51.13%2BPM.png)![Hunchback](https://lh3.googleusercontent.com/-tmW3PtmiB9Q/V1TMAbuCXDI/AAAAAAABeVM/lnGkoCUIynICQLq0gdOBBlMNTHGWiyZ5ACCo/s144/Screen%2BShot%2B2016-06-05%2Bat%2B9.51.33%2BPM.png)![Snoopy](https://lh3.googleusercontent.com/--9xseeTKSSM/V1yMXFsB3rI/AAAAAAABeWc/BZE246LKe-EHD8txSydNa-OSAtruqwDWQCCo/s144/Screen%2BShot%2B2016-06-11%2Bat%2B3.08.06%2BPM.png)

* [Giana Sisters+.d64](../../raw/master/disks/trainer-gianasisters+ ERA.d64)
* [Galaxy+.d64](../../raw/master/disks/trainer-galaxy+ ERA.d64)
* [Hard Hat Mack+.d64](../../raw/master/disks/trainer-hardhatmack+ ERA.d64)
* [Hunchback+.d64](../../raw/master/disks/trainer-hunchback+ ERA.d64)
* [Snoopy+.d64](../../raw/master/disks/trainer-snoopy+ ERA.d64)

# Recracks

I also did some recracks for c64 games. _Recrack_: that lame activity that consists in replacing an intro done by someone else with another intro done by yourself.

* [Airborne Ranger.zip](../../raw/master/disks/recrack-airborne ranger ERA.zip)
* [Alien Syndrome.d64](../../raw/master/disks/recrack-alien syndrome ERA.d64)
* [Boulder Dash 16.d64](../../raw/master/disks/recrack-boulderdash16 ERA.d64)
* [Celebration Kit.d64](../../raw/master/disks/recrack-celebration kit ERA.d64)
* [Double Dragon II.d64](../../raw/master/disks/recrack-double dragon II ERA.d64)
* [Elite.d64](../../raw/master/disks/recrack-elite ERA.d64)
* [Fourth and Inches.d64](../../raw/master/disks/recrack-fourth and inches ERA.d64)
* [Jordan vs. Bird.zip](../../raw/master/disks/recrack-jordan vs bird ERA.zip)
* [Maniac Mansion.zip](../../raw/master/disks/recrack-maniac mansion ERA.zip)
* [MULE.d64](../../raw/master/disks/recrack-mule ERA.d64)
* [Ninja.d64](../../raw/master/disks/recrack-ninja ERA.d64)
* [Pro Tennis Tour.d64](../../raw/master/disks/recrack-pro tennis tour ERA.d64)
* [Sim City.d64](../../raw/master/disks/recrack-simcity ERA.d64)
* [Soccer Simulator.d64](../../raw/master/disks/recrack-soccer simulator ERA.d64)
* [Stellar 7.d64](../../raw/master/disks/recrack-stellar 7 ERA.d64)
* [Turbo Outrun.d64](../../raw/master/disks/recrack-turbo outrun ERA.d64)
* [Tusker.d64](../../raw/master/disks/recrack-tusker ERA.d64)
* [TV Sports Football.zip](../../raw/master/disks/recrack-tv sports football ERA.zip)
* [Wings of Fury.d64](../../raw/master/disks/recrack-wings of fury+4 ERA.d64)


# Trivia

* Why that weird color palette? Because I developed them using a black-and-white TV. I never had the chance to play them on a color TV... until today :-)
* "RQ progs" comes from _Ricardo Quesada Programs_
* "Erasoft" comes from _Erasure_ + _software_. I used to be an Erasure fan back then
* My "circle + rectangle + triangle" logo is a _remix_ of the Electronic Arts logo from the 80's. I used to be an EA fan back then
* My Erasoft logos were based on Erasure logos
* One game is called _Race_ and another one is called _The Race_. Kind of confusing, right? A better name would have been _Race 2_.
* Each game was packed in a d71 image for convinience. Double-clicking on them should launch [VICE](http://vice-emu.sourceforge.net/) emulator. But they can be packed in a .d64 image if needed.
* All games were developed in a NTSC machine, so tell VICE to emulate NTSC video.


# Looking for more ?

Here is the complete collection of my games and intros from 88' to 92':

DISCLAIMER: Some games / intros might require special commands in order to run correctly. Don't expect anything special.


* All my Commodore 64 games: [complete_rq_games_c64.d64](../../raw/master/disks/complete_rq_games_c64.d64)
* All my Commodore 128 games: [complete_rq_games_c128.d71](../../raw/master/disks/complete_rq_games_c128.d71)
* All my Commodore 64 intros:
[complete_rq_intros_c64.d64](../../raw/master/disks/complete_rq_intros_c64.d64)
* All my Commodore 128 intros
[complete_rq_intros_c128.d71](../../raw/master/disks/complete_rq_intros_c128.d71)
