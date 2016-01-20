---
layout: post
title: Xbox One Dev at GDC
author: Michael Quandt
---
One of the things I've been meaning to do recently is post about the ID@Xbox presentations that were on at GDC this year. Quite a lot of information was provided outside of the standard NDA that people have to sign at the official ID@Xbox events and so I thought that I should put this information online somewhere so that others can find out what was presented. (The sessions were not recorded) I did not attend all sessions and so my notes are fairly incomplete and lack information about the Kinect and LIVE SDK.

This post is effectively a dump of my notes. Short and sweet. As far as I'm aware, the information is still correct at the time of writing. At the very least the information was correct at GDC.

The spec available to developers on the Xbox is:

* 5GB for Games
* 6 logical cores (4 dedicated, #5 & #6 share cache with OS)
   * Quad-core CPU - 2 logical cores/threads per physical core
* DX11.1 level GPU
* 32MB ESRAM (similar to EDRAM in Xbox 360, but more)

###APIs
####Available
* Direct3D 11.1 (with extensions)
* DXGI 1.2
* Custom Controller API (not XInput)
* HTML/JavaScript

####Unavailable
* Direct2D
* DirectWrite
* (Games Only) XAML
* (WinRT) Security
* (WinRT) Management
* (WinRT) Globalization
* (WinRT) Graphics

All code is x64, and by default you use 16 byte alignment.

There are two modes, full and constrained. If you have used an Xbox One, constrained mode is when your game/app runs inside the main tile on the dashboard. When in this mode you receive less resources as cores 5 & 6 are folded into cores 3 & 4, so you can continue to use the same code however 3 & 4 will have much higher contention. Cores 1 & 2 will always be safe and dedicated.

###Distribution
This is a small section, however a quick note for those who know how Windows 8 handles AppX packages and distribution.
The Xbox One deploys each game with a copy of the operating system, similar to how previous generations of consoles have handled things. This allows games to ship with a specific version and run in an environment they have tested for. This way future changes won't break the game.
To handle the size for updates, the AppX is generated in a chunked format to allow for the early play feature, as well as differential updates to reduce the update size for players, and during development.
Alongside this, during development you can "stream" the game from your development PC. This of course requires a continuous connection to the PC, however it reduces iteration time when debugging. If you want to disconnect the Xbox and take it somewhere (to show off your game or play it without a dev PC connected) you can deploy the entire game package, however this will take much longer.

###Tools
As of GDC, development was done with Visual Studio 2012 and a special version of PIX is included for debugging and profiling on the console. Development is done in a simiar fashion to Windows 8 development on a remote machine. Companion apps can be developed in a similar way however these use the VS Graphics Debugger instead. The XDK offers a new graphics context named *ID3DXboxPerformanceContext* which has Xbox specific extensions that can be used. Everything else is Direct3D 11.1.

###Changes/Disclaimer
At the time of writing, Phil Spencer just announced changes and updates to the XDK that improve development and performance. As a result we can see that the tools are changing and improving over time, so parts of this post may no longer be valid.