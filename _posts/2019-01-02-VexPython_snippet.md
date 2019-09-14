---
layout: post
title: Vex, python snippet 
tags: [Houdini]
categories:
- blog
---

-------


```py

node = hou.pwd()
geo = node.geometry()


for prim in geo.prims():
    path = prim.attribValue("path")
    newpath = path[:path.rfind("/")]
    prim.setAttribValue("path", newpath)

```

## Centre Pivots

Sets pivot transforms to $CEX, $CEY, $CEZ on selected nodes
```py
# Centre pivots
import hou

sel = hou.selectedNodes()
for nodes in sel:
    nodes.parm('px').setExpression('$CEX')
    nodes.parm('py').setExpression('$CEY')
    nodes.parm('pz').setExpression('$CEZ')

```

## Find/Replace Parameter Expression

Will find/replace strings within selected nodes’ parameters’ expressions
```py
import hou

sel = hou.selectedNodes()
        
dialog = hou.ui.readMultiInput('Find/Replace In Expression', input_labels=['Find: ', 'Replace: ',], buttons=("Find/Replace", "Cancel"),
     severity=hou.severityType.ImportantMessage, title='Find/Replace', close_choice=1)

find = dialog[1][0]
replace = dialog[1][1]


if dialog[0] == 0:
    for n in sel:
        for parms in n.parms():
            try:
                newString = str(parms.eval()).replace(find, replace)
                parms.set(newString)
            except:
                print ''
            try:
                newExpression = str(parms.expression()).replace(find, replace)
                parms.setExpression(newExpression)
            except:
                print ''
        
```

## Match Parameters

Select two nodes and this script will copy all parameters from the first selected node to the second selected
```py
# --- This tool will match all parameters from the first selected node to the second.
# --- good for copying ramps as well as the regular stuff.

def matchParams():
    import hou

    value = 0
    sel = hou.selectedNodes()

    if len(sel) == 2:
        source = sel[0]
        dest = sel[1]
        for param in source.parms():
            sourceParm = param.name()  # source parameter
            destParm = dest.parm(sourceParm)  # Destination parameter
            try:
                destParm.deleteAllKeyframes()
            except:
                value += 1
            try:
                sourceLanguage = param.expressionLanguage()
                destParm.setExpression(param.expression(), language=sourceLanguage)

            except:
                value += 1
            try:
                destParm.set(param.eval())
            except:
                value += 1
            try:
                destParm.set(param.unexpandedString())
            except:
                value += 1

            if param.isLocked() == 'True':
                destParm.lock(on)
    else:
        print 'Select two nodes to match parameters'

matchParams()
```

## Toggle Update Mode

This script will toggle between Manual and Auto Update modes
```py
if hou.ui.updateMode() == hou.updateMode.AutoUpdate:
    hou.ui.setUpdateMode(hou.updateMode.Manual)
else:
    hou.ui.setUpdateMode(hou.updateMode.AutoUpdate)
```

## Set Camera Parameters

A short example to set all camera parameters – specifically resolution and icon scale
```py
import hou
''' This script will set all cameras res to those determined below
    and icon scale'''

resx = "1920"
resy = "1080"
iconsize = "100"

cameras = hou.nodeType(hou.objNodeTypeCategory(), "cam")
cameras.instances()

for cams in cameras.instances():
    cams.parm("resx").set(resx)
    cams.parm("resy").set(resy)
    cams.parm("iconscale").set(iconsize)
```
