---
title: Review - Direct3D Rendering Cookbook
layout: post
author: Michael Quandt
---
### Direct3D Rendering Cookbook
![Book Cover Image](http://mquandt.com/blog/content/images/2014/Apr/7101OT_Direct3D-Rendering-Cookbook.png)

Author: **Justin Stenning**
*Packt Publishing*  
[Book Website](http://www.packtpub.com/direct3d-rendering-cookbook/book)

One of the areas I avoided covering in too much detail in my book was the area of 3D rendering. This is an area that can become fairly complex and requires knowledge of pipelines and other systems that can get in the way of learning the basics about game development. Naturally however, many will want to expand into this area once they have a grasp of the basics. Thanks to Packt, I will be taking a look at a book that may help with this, the Direct3D Rendering Cookbook, by Justin Stenning.

#### What does the book cover?
The Direct3D Rendering Cookbook walks readers through the development of a 3D renderer, covering each of the shader stages available in Direct3D 11.2, and includes some examples and standard techniques that may be implemented for each stage. The book uses C# along with the SharpDX library to learn about the different stages of the graphics pipeline, before expanding into shading (Lambert, Blinn and Blinn-Phong) and character animation. From there the newer shader stages are introduced and the reader is exposed to tessellation and GPGPU techniques that they can then implement as domain, hull and compute shaders. Additionally the book looks at how to fit all of this into a Windows 8.1 store application, and runs through the tools available in Visual Studio 2012/2013 such as the mesh compiler and graphics debugging tools.
Alongside this the book also looks at some non-graphical techniques such as multi-threaded rendering and GPGPU physics, which is a nice inclusion. Deferred rendering (shading to be specific) is also described in its own chapter, bringing together some techniques and looking at an alternative to traditional forward rendering.

#### What should you already know?
One important thing to note is that the code provided in this book is all written in C#, which makes learning and understanding easier for many used to Microsoft platforms, however those learning game development using C++ or other languages will need to translate the samples before they can use them. This is not necessarily a major issue as the theory is the key part, however you may need a reference on the side as SharpDX hides many of the complexities that come from a C++/COM API so that it can fit into the C# and .NET universe.
As the name implies, this book focuses on 3D rendering, and does not limit itself to games. The basics such as programming and structuring games are assumed knowledge.

#### Thoughts
If you saw “cookbook” in the title and are looking for a collection of techniques that you can use for rendering, this book may not be your best fit as it spends a fair amount of time covering Direct3D setup, basic techniques and supporting concepts such as physics and multi-threaded rendering. That said, the book is a great starting point for those looking to jump into 3D rendering, and even remains relevant once the basics have been covered by providing reference information about advanced shaders and techniques that you may want to make use of later.
This is also one of the few books I have seen that covers multi-threaded rendering (increasingly relevant in modern engines), deferred shading and GPGPU techniques (physics even) outside of expert reference books such as what you would find in the GPU Pro series.

The majority of the book uses sets of instructions to implement each technique, with explanations left to the end, once you’re done implementing the technique. This may force you to jump around a bit if you do not understand certain parts of the technique and can’t wait until you’ve finished every step. This book is most effective if you read ahead, gain an understanding of the technique and then follow the steps to implement. You won’t be flipping pages back and forth, and all of the instructions are in one place, making it much easier to find each step.

As you work through each technique and concept the author also provides some extra reading on the topic, which enables you to learn further or find answers to any questions you may have.

I would recommend this book to anyone who is interested in having a solid resource for 3D development that will last them past the basics. You will need to understand C# if you do not already to get the most out of this book, and if you want to use this for game development then you will need to look elsewhere for every other aspect, however supplemented by other learning, this book can be very useful.

#### Where can I get it?
The paper and electronic versions of the book can be found at the [Packt Publishing Website](http://www.packtpub.com/direct3d-rendering-cookbook/book), [Amazon](http://www.amazon.com/dp/1849697108/) or a number of other stores (all listed on the Packt website).

*My review is based on an eBook copy provided to me for free by Packt Publishing for review purposes.*