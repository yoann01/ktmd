---
layout: post
title: physically based Rendering texturing workflow
tags: [PBR, Materials]
categories:
- blog
---
# PBR Spec/Rough and Rough/Metal Workflow

## Metal Rough Worfkow

![test image size](https://meshlogic.github.io/posts/blender/materials/nodes-pbr-basic-shader/pbr_maps.png)

### Base Color

Raw color with no lighting information. Small amount of ambient occlusion can be baked in if using it for micro-surface occlusion. The color range for dark values should stay within 30-50 RGB. Never have dark values bellow 30 RGB. The brightest color value should not go above 240 RGB.

### Roughness

Describes the **microsurface** of the object. White 1.0 is rough and black 0.0 is smooth. The microsurface if rough can cause the light rays to scatter and make the highlight appear dimmer and more broad. The same amount of light energy is reflected going out as coming into the surface. This map has the most artistic freedom. There is no wrong answers here. This map gives the asset the most character as it truly describes the surface e.g. scratches, fingerprints, smudges, grime etc.

### Normal

Normal map.

### Metallic

Tells the shader if something is metal or not. Raw Metal = 1.0 white and non metal = 0.0 black. There can be transitional gray values that indicate something covering the raw metal such as dirt.

>  With **metal/rough**, the areas indicated as metal in the metallic map have a corresponding metal reflectance value in the base color map. The metal reflectance value in the base color needs to be a measured real-world value. Transitional areas in the metal map (not raw metal 1.0 white) need to have the metal reflectance value lowered to indicate that its reflectance value is not raw metal.

Also, with metal/rough, you only have control over metal reflectance values. The dielectric values are set to 0.04 or 4% which is most dielectric materials. The dielectric is hard-coded by the shader and you don’t need to set it in Substance. Some shaders add a specular control that allows you to change the fresnel reflectance value at 0 degrees.

---

## Specular Glossiness Workflow



### Diffuse 

Raw color with no lighting information. Small amount of ambient occlusion can be baked in if using it for micro-surface occlusion. The color range for dark values should stay within 30-50 RGB. Never have dark values below 30 RGB. The brightest color value should not go above 240 RGB.

### Glossiness 

This map is the **inverse of the roughness map**. White 1.0 is smooth and 0.0 black is rough. Describes the microsurface of the object. The microsurface if rough can cause the light rays to scatter and make the highlight appear dimmer and more broad. The same amount of light energy is reflected going out as coming into the surface. This map has the most artistic freedom. There is no wrong answers here. This map gives the asset the most character as it truly describes the surface e.g. scratches, fingerprints, smudges, grime etc.

### Specular 

This map contains the reflectance information for both metal and dielectrics (non metal) surfaces. This is a key difference in the metal/rough and spec/gloss workflows. The same rules apply. You need to use measured values for metals and most all dielectrics will fall with the 0.04 - 4% range. If there is dirt on the metal, the reflectance value needs to be lowered as well. However, you can add different values in the specular map for dielectric materials since you have control to author the map.

###  Normal 

Normal map

---

Thanks to:

 Wes McDermott [allegorithmic ](https://www.allegorithmic.com/)
