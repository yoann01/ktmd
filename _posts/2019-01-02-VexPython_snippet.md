---
layout: post
title: Vex, python snippet 
tags: [Houdini]
categories:
- blog
---

-------
# Python


```py

node = hou.pwd()
geo = node.geometry()


for prim in geo.prims():
    path = prim.attribValue("path")
    newpath = path[:path.rfind("/")]
    prim.setAttribValue("path", newpath)

```

