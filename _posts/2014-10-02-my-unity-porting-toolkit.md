---
layout: post
title: My Unity Porting Toolkit
author: Michael Quandt
---
Over the last year and a half I've been involved in porting many games over to the Windows (tablet/desktop) and Phone platforms with [Marker Metro](http://markermetro.com/). (Some examples in my [portfolio](http://mquandt.com/portfolio.html))

While doing this I have built up a small set of invaluable tools to assist with the task. I decided I should probably post this small list up in case some of these are new to anyone out there.

###What I Use
* [Visual Studio 2013 Update 3](http://www.visualstudio.com/) (Pro or higher required for plugins)
* [Visual Studio Tools for Unity](http://unityvs.com/) (aka UnityVS)
* [Bing Developer Assistant](http://visualstudiogallery.msdn.microsoft.com/a1166718-a2d9-4a48-a5fd-504ff4ad1b65)
* [.NET Portability Analyzer](http://blogs.msdn.com/b/dotnet/archive/2014/08/06/leveraging-existing-code-across-net-platforms.aspx)
* [NuGet](http://www.nuget.org) (Comes with Visual Studio 2013)

So what do I use each of these for? Well Visual Studio is obvious, but the rest may not be, especially for developers not involved in the Microsoft development world.

###What Are These Things?
Let's start with the **Visual Studio Tools for Unity** (UnityVS). This plugin comes in two parts, the extension for Visual Studio (2010/2012/2013) and a Unity Package that you add to your project. When combined this tool allows you to write your scripts using Visual Studio, and even debug in editor. But the big benefit that isn't mentioned, is the IDE support for scripts, even if you aren't working in the editor. Unity for Windows Store and Windows Phone allows developers to debug on device using Visual Studio, and to do that you need to add the MonoDevelop or UnityVS project to your solution. This plugin allows you to edit those scripts with full support in the IDE, making the edit > rebuild > run loop much faster.

Next is the **Bing Developer Assistant**. This little extension provides inline code snippets from the web for APIs that you may want to use. When I say inline, I mean it includes them alongside your intellisense drop-down, making it really easy to figure out how you're supposed to use a new API. This is very important when porting games because you will spend a fair bit of time converting code to work with new APIs and many of them may be completely new to you. Save yourself some time searching for examples online by letting this extension find them for you.

When you start work on a project, or are trying to evaluate the amount of work required, the **.NET Portability Analyzer** comes in handy. This little tool takes a look at your code and determines how much of it will **just work** on Windows 8. When it finds code that doesn't work, it will let you know so you can figure out how much work is required, or where you need to start. When combined with the porting guide and samples [here](http://unity3d.com/pages/windows/porting) you can get off to a good start.

Finally, if you haven't encountered NuGet before, I strongly encourage you to take a look. NuGet can be considered the apt-get (package manager) for development libraries. With NuGet I can easily find and download libraries as required, all from within Visual Studio, and better yet when I commit that to source control I only need to commit the package list - NuGet will handle re-downloading any packages that are missing during the build process.

These are the main tools I use when working on a game conversion, and I strongly recommend each and every one of them.

Do you have any extensions, tools, or plugins (Unity, Visual Studio, anything else?) that you use for game development or converting games. Let me know on twitter ([@quandtm](https://www.twitter.com/quandtm)), because I'm always looking for new tools to make the process easier.