SDLPAL
======

[![Join the chat at https://gitter.im/sdlpal/sdlpal](https://badges.gitter.im/sdlpal/sdlpal.svg)](https://gitter.im/sdlpal/sdlpal?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)
[![Travis CI](https://travis-ci.org/sdlpal/sdlpal.svg?branch=master)](https://travis-ci.org/sdlpal/sdlpal)
[![Build status](https://ci.appveyor.com/api/projects/status/wc8r3qlqmh5q6j1c?svg=true)](https://ci.appveyor.com/project/palxex/sdlpal-itfml)

***SDLPAL*** is an SDL-based open-source cross-platform reimplementation of the classic Chinese RPG game *Xiān jiàn Qí Xiá Zhuàn (Chinese: 仙剑奇侠传/仙劍奇俠傳)* (also known as *Chinese Paladin* or *Legend of Sword and Fairy*, or *PAL* for short).


LICENSE
=======

SDLPAL is originally created by [Wei Mingzhi](https://github.com/CecilHarvey) from 2009.
```
Copyright (c) 2009-2011 Wei Mingzhi <whistler_wmz@users.sf.net>.
Copyright (c) 2011-2017 SDLPAL development team.
All rights reserved.
```
SDLPAL is distributed under the terms of GNU General Public License, version 3 (or any later version) as published by the Free Software Foundation. See [gpl.txt](https://raw.githubusercontent.com/sdlpal/sdlpal/master/gpl.txt) for details.

Many of the ideas of this program are based on documents from [PAL Research Project](https://github.com/palxex/palresearch). Portions of the code are based on the work done by Baldur and [louyihua](https://github.com/louyihua), and the resampler code is based on the code in [Kode54](https://github.com/kode54)'s [foo_input_adplug](https://github.com/kode54/foo_input_adplug) project.

This program made extensive use of the following libraries:
* [SDL](http://www.libsdl.org/)
* [SDL_mixer](http://www.libsdl.org/projects/SDL_mixer/)
* [Adplug](http://adplug.sourceforge.net/)
* [libmad](http://www.underbit.com/products/mad/)
* [libogg & libvorbis](http://www.vorbis.com/)
* [FLTK](http://www.fltk.org)
* [DOSBOX project](http://www.dosbox.com) and [MAME project](http://mamedev.org/) for codes of some the OPL simulation cores

Please see [AUTHORS.txt](https://raw.githubusercontent.com/sdlpal/sdlpal/master/AUTHORS.txt) for additional authors.

This program does **NOT** include any code or data files of the original game, which are proprietary and copyrighted by SoftStar Inc.


Building the game
=================

The steps for building SDLPAL varies in different platforms. Currently, SDLPAL supports most desktop platforms including *Windows* (including *Windows Store*), *Linux* and *macOS*, as well as most popular mobile platforms including *Android*, *iOS* and *Windows Phone*. It is also ported to several *home console* platforms.

Windows
-------

### Visual Studio

To build SDLPAL as a Windows **desktop** app, you can use ***Microsoft Visual Studio 2015*** or ***Microsoft Visual Studio 2017*** (the support of *Visual Studio 2013* is **deprecated** now and will be removed in future) to open the solution file *`sdlpal.sln`* under the *`win32`* directory. As a dependency, you need to have [SDL 2.0](https://www.libsdl.org/download-2.0.php) development or source files installed at the *`SDL2`* directory under the source tree.

To build SDLPAL as a **Universal Windows Platform** app, you can use ***Microsoft Visual Studio 2015*** or ***Microsoft Visual Studio 2017*** to open the solution file *`SDLPal.UWP.sln`* under the *`winrt`* directory. As a dependency, you need to have [SDL 2.0](https://www.libsdl.org/download-2.0.php) **source** files installed at the *`SDL2`* directory under the source tree.

There are also solution files for building traditional **Windows (phone) store app** under the *`winrt`* directory, but they are deprecated and will be removed in future.

### MinGW

To build SDLPAL as a Windows **desktop** app, you can also use ***MinGW***. Steps for building under MinGW varies depends on the compiling environment you have:

* If you need to compile SDLPAL under **Windows** shell environment, please go to the root of the source code tree and type:
```shell
$ cd win32
$ make -f Makefile.mingw
```

* If you need to compile SDLPAL under **msys** shell environment, please go to the root of the source code tree and type:
```shell
$ cd win32
$ make
```

* If you need to cross-compile SDLPAL under **Linux** shell environment, please go to the root of the source code tree and type:
```shell
$ cd win32
$ make HOST=i686-w64-mingw32-  # This builds a 32-bit executable. To build a 64-bit executable, replace 'i686' by 'x86_64'.
```


Linux or Unix
-------------

To build the game, please go to the root of the source code tree and type:
```shell
$ cd unix
$ make
```
You also need to have SDL 2.0 development files installed in the system. The compiled executable should be generated with the filename *`sdlpal`* at the current directory. By default, SDLPAL uses the FLTK library to provide setting GUI at launch. If you do not want to use the library, please define he macro `PAL_NO_LAUNCH_UI` in the `Makefile`. SDLPAL should also be able to compile and run under other Unix-like systems, however it's not tested.


macOS (OS X)
------------

To compile, open *`Pal.xcodeproj`* with `Xcode`, and click Build. You need to have SDL framework installed at *`/Library/Frameworks`*.

iOS
---

To compile, open the project *`ios/SDLPal/SDLPal.xcodeproj`* with `Xcode`, and click Build. You need to have SDL2 **source files** (not development files) extracted in the *`SDL2`* folder.

Android
-------

To build the game, please go to the root of the source code tree and type:
```shell
cd android/jni
ndk-build
cd ..
ant debug
```
You need to have SDL2 **source files** (not development files) extracted in the *`SDL2`* folder.

Nintendo 3DS
------------

To build the game, please go to the root of the source code tree and type:
```shell
cd 3ds
make
make cia
```
You need to have *DevkitPro ARM* and *SDL 1.2* for 3DS portlib installed. The compiled executable should be generated with the filename *`sdlpal`* at the current directory.

Other platforms
---------------

To be written.


Choosing the battle system
==========================

By default, SDLPAL builds a *"classic"* turn-based battle system which is designed to be 100% the same as the original game.

SDLPAL also provides a revised battle system (***deprecated*** and will be removed in future) which is more exciting yet somewhat harder than the original game. If you prefer this battle system, please define the macro `ENABLE_REVISIED_BATTLE` in *`Makefile`* or in *`common.h`* and recompile the project.


Running the game
================

The data files required for running the game are not included with the source package due to copyright issues, so you need to obtain them from a licensed game copy before you can run the game.

To run the game, copy all the files in the original game CD to a directory, then copy the built SDLPAL executable to the same directory, and run the executable.

Note that the filenames of data files should be all in lower-case under systems that use case-sensitive filesystems such as Linux or other Unix-like operating systems.


Configuring the game
====================

PAL has several variants using different and incompatible resource files, and SDLPAL supports several configuration options for supporting such variants.

To set these configuration options, create a file named as *`sdlpal.cfg`* (make sure to use lower-case file name in case-sensitive filesystems) in the game directory created by the above step. If no configuration file exists, SDLPAL uses default values that supports the resources from original DOS version.

Please refer to the file [sdlpal.cfg.example](https://raw.githubusercontent.com/sdlpal/sdlpal/master/sdlpal.cfg.example) for configuration file format.


Reporting issues
================

If you find any issues of SDLPAL, please feel free to report them to the development team through Github's issue tracking system using either English or Chinese.


Contributing to the game
========================

Any original code & documentation contributions are welcomed as long as the contributed code & documentation is licensed under GPL. You can use Github's pull request system to submit your changes to the main repository here. But remember, as a step to keep the quality of code, you should write corresponding unit tests before your changes can be merged. The guidance of writting unit tests can be found [here](https://github.com/sdlpal/sdlpal/tree/master/tests).
