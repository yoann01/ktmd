---
layout: post
title: Zbrush startup macro
tags: [Zbrush]
categories:
- blog
---

> - Create a text file in the folowing folder **C:\Program Files (x86)\Pixologic\ZBrush 4R7\ZStartup\Macros\Misc**
> - Call it whatever you want (mine is yg_setupMacro.txt :shipit:)
> - copy and past the following code

```js
//ZBRUSH MACRO - Recorded in ZBrush version 4.73
[IButton,???,"Zbrush custom startup macros.",
[IShowActions,0]
[IConfig,4.73]

// Set Document Backgroung/size
[ISet,Document:Rate,0]
[ISet,Document:Width,2046]
[IPress,Document:Resize]

// Turn Off Spotlight projection
[IUnPress,Brush:Samples:Spotlight Projection]

// Configure LightBox
[IUnPress,Preferences:Lightbox:Open At Launch]
[ISet,Preferences:Lightbox:Glow Brightness,0]
[ISet,Preferences:Lightbox:Glow Opacity,0]

// Set Quicksave options
[ISet,Preferences:QuickSave:Maximum Duration,40]
[ISet,Preferences:QuickSave:Rest Duration,5]

// Set Base material
[IPress,Material:BasicMaterial]
[IColorSet,128,128,128]
[ISet,Material:Wax Modifiers:Strength,55]
[ISet,Material:Modifiers:Ambient,0]
[ISet,Material:Modifiers:Specular,20]

// ACtivate wax preview
[IPress,Render:Render Properties:WaxPreview]
[ISet,Render:Preview Wax :Strength,0.65]
[ISet,Render:Preview Wax :Temperature,7]
[IPress,Render:Render Properties:Shadows]

[IPress,Tool:Sphere3D]
[ISet,Draw:Angle of View,27]
[IPress,Brush:ClayTubes]
[ISet,Alpha:Modify:Blur,2]
[ISet,Stroke:Roll Dist,5]
[IPress,Color:Clear]
[IUnPress,Transform: Edit]
[IPress,Color:Clear]
]
```
> - Got to **C:\Program Files (x86)\Pixologic\ZBrush 4R7\ZScripts**
> - Open the DefaultZScipt.txt
> - add the following

```
[If,1,
[IPress,Macro:Macros:Misc:yg_setupMacro]
]
[pd]
```
