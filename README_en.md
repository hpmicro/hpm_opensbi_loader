# OpenSBI Loader

## Overview

OpenSBI Loader is a simple loader for OpenSBI. It assumes that the mirror image distribution in Flash is as follows:

|address|image name|
|---|---|
|0x80010000|OpenSBI|
|0x80040000|Linux Kernel|
|0x80310000|Linux DTB|

If the mirror image addresses in Flash are inconsistent, the macro definitions in the source code can be modified to fit your own needs.

## Things that must be done
- setup uart0 pinmux and set its clock frequency to 24MHz, so opensbi can init uart0 currently. Otherwise OpenSBI's console maybe not work.
- Initialize the SDRAM
- Copy the OpenSBI image to the address 0x00000000
- Copy the Linux Kernel image to the address 0x40000000
- Copy the Linux DTB image to the address 0x40300000
- Disable interrupt vector mode
- Make sure that the loader does not use the memory area that other image uses

## Board Setting

No special settings

## Running the example
```
OpenSBI v0.6-4-gc335500
   ____                    _____ ____ _____
  / __ \                  / ____|  _ \_   _|
 | |  | |_ __   ___ _ __ | (___ | |_) || |
 | |  | | '_ \ / _ \ '_ \ \___ \|  _ < | |
 | |__| | |_) |  __/ | | |____) | |_) || |_
  \____/| .__/ \___|_| |_|_____/|____/_____|
        | |
        |_|

```
