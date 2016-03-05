---
layout: post
author: Michael Quandt
title: Compiling Vulkan from Scratch
---
# Introduction & Motivation #

*Works for SDK version 1.0.3*

A few weeks ago Vulkan 1.0 was released to the public, which marked the first time those outside of Khronos saw the API and SDK (provided by LunarG). If you have a relatively recent Ubuntu (or debian) OS install, or Windows, you can just download the SDK from the (Official Website)[http://vulkan.lunarg.com].

At Animal Logic we use an older version of CentOS that aligns with the VFX reference platform rather than the latest and greatest. This however means that our version of GLIBC is older than what you may find in more recent Ubuntu installs, which LunarG targetted for the Linux SDK.

Thankfully the open nature of Vulkan and Khronos means the source code we care about, for the loader and tools, is provided on Github. This means that we can compile the files ourselves.

# Loaders and Layers #
First lets take a quick look at some design decisions, which may inform what you want to compile and use.

To allow for extension in future, Vulkan adopts the extension model that OpenGL has used successfully over its many years. IHVs can provide implementations of extensions that are experimental or unique to their hardware, and ISVs can detect if these exist and use the new functionality without requiring a new version of OpenGL (or in this case Vulkan).

Vulkan has gone a step further by defining a layer system that allows the developer to add layers between their application and the underlying driver implementation. These layers enable powerful new development and debugging options without requiring intrusive changes to the application or driver code.

These two elements are connected and powered by the Vulkan loader (libvulkan.so on Linux and Vulkan-1.dll on Windows). This loader provides the base API spec as well as the function pointer discovery required for extensions. This is the main thing we need to build to use Vulkan on a system with a different version of GLIBC, and this is the only thing we need to run Vulkan with its base specifications. If we want to enable the use of GLSL, or the debugging layers, then we will need to compile some other tools which will fill out what the SDK normally provides.

# Requirements #

* git
* python 3.x
* cmake
* clang 3.4+ (gcc may work however I have not tried this)

# Steps #

## Get the Source ##

First clone the following repositories from github:
(https://github.com/KhronosGroup/Vulkan-LoaderAndValidationLayers.git)[https://github.com/KhronosGroup/Vulkan-LoaderAndValidationLayers.git]
(https://github.com/LunarG/VulkanTools.git)[https://github.com/LunarG/VulkanTools.git]

## Update & Build Dependencies ##

Inside Vulkan-LoaderAndValidationLayers, run `./update_external_sources.sh`

This will download the repositories the loader and validation layers require (SPIR-V etc) and compile them, so ensure that clang, cmake and python are in your path.

Once this is done, move to the VulkanTools repository and do the same.

## CMAKE Configuration ##
This article focuses on GLIBC 2.12, however it should apply to most versions, and this is probably the section that will differ the most, so please test and remember that your mileage may vary.

In 2.12 the string format macros are not globally defined, as the SDK expects. If you see any errors that require macros such as PRIx64, just add the following lines to the CMakeLists.txt file in both of the repositories you cloned:

```
add_definitions(-D__STDC_FORMAT_MACROS)
```

This line will enable those macros. You may also want to disable compilation of vkjson_info and the demos as some of them require the alignedmalloc function that was addded to a more recentl glibc (but which is missing from 2.12). To do this, just add -DBUILD_DEMOS_off and -DBUILD_VKJSON=off to the cmake command line we will execute later.
