---
layout: post
title: Neural Network Ambient Occlusion for Unity via @_kzr
tags: [UNITY, Neural network]
categories:
- blog
---
# Neural Network Ambient Occlusion

![neural network AO](https://camo.githubusercontent.com/b67c563e892a460e2bdd7db62424fdb012104c11/687474703a2f2f696d6775722e636f6d2f4d4b72303432746c2e706e67)


At SIGGRAPH Asia this year I am presenting Neural Network Ambient Occlusion. 
This short paper uses Machine Learning to produce ambient occlusion from the screen space depth and normals. 
A large database of ambient occlusion is rendered offline and a neural network trained to produce ambient 
occlusion from a small patch of screen space information. This network is then converted into 
a fast runtime shader that runs in a single pass and can be used as a drop-in replacement 
to other screen space ambient occlusion techniques.

[Keijiro Takahashi ](https://github.com/keijiro/NNAOTest)
