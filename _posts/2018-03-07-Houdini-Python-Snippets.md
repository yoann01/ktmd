---
layout: post
title:  Houdini HOM 
tags: [Houdini, Python]
categories:
- blog
---


# HOM part 1

### **Overview**

The Houdini Object Model (HOM) is an application programming interface (API) that lets you get information from and control Houdini using the **Python scripting language**. 

HOM replaces the functionality of Houdiniâ€™s previous scripting solutions, the **expression language** and **HScript**.

**Node Createtion**

>Open the python shell, create a geo sop in the shell enter:
```sh
>>> hou.node('/obj/geo1')
<hou.ObjNode of type geo at /obj/geo1>
>>> n = hou.node('/obj/geo1')
>>> n.name() 
'geo1'
>>> n.setName('Object1')
>>> t1 = n.createNode('xform')
>>> t1.moveToGoodPosition()
<hou.Vector2[0, 0]>
>>> t1.destroy()
```
```sh
>>> obj = hou.node('/obj')
>>> obj 
<hou.Node at /obj>
>>> obj.createNode('geo')
<hou.ObjNode of type geo at /obj/geo1>
>>> n = hou.selectNodes() 
>>> n
<hou.ObjNode of type geo at /obj/geo1>
>>> n.children()
(<hou.SopNode of type file at /obj/geo1/file1>,)
>>> for i in n.children():
...     i.destryo()
...
>>> obj.createNode('geo', run_init_script=0)

```
**Node Parameter**
```sh
>>> n = hou.node("/obj").createNode("geo")
>>> n.setCurrent(1)
>>> n.parm("tx")
<hou.Parm tx in /obj/geo3>
>>> tx=n.parm("tx")
>>> tx.set(0.1)
>>> tx.set(1)
>>> tx.eval()
1.0
>>> tr = n.parmTuple("t")
>>> tr
<hou.ParmTuple t in /obj/geo3>
>>> tr.set([1,1,1])
>>> tr.set(hou.Vector3(1.2, 2.2, 1.0))
>>> hou.parm("/obj/geo3/tx")
<hou.Parm tx in /obj/geo3>
>>> hou.ch("/obj/geo3/tx")
1.2
>>> 
```

```sh
>>> geo=hou.node('/obj/geo1')
>>> box = geo.createNode('box')
>>> t1 = geo.createNode('xform')
>>> t1.moveToGoodPosition()
<hou.Vector2 [0, 0]>
>>> t1.setInput(0, box)
>>> t1.parm('tx').set(1)
>>> t2 = box.createOutputNode('xform')
>>> t2.parm('tx').set(-1)
>>> m = geo.createNode('merge')
>>> m.moveToGoodPosition()
<hou.Vector2 [0, 0]>
>>> m.setNextInput(t1)
>>> m.setNextInput(t2)
>>> m.setDisplayFlag(1)
>>> m.setRenderFlag(1)
>>> m.createOutputNode('null')
>>> m.setName('OUT_TEST')
>>> m.outputs()
>>> m.inputs()
>>> m.inputs()[0]
```

**Connect nodes**

>add a materialBuilder in **shop** context

```sh
>>> n1 = hou.node('/shop/vopmaterial1/lambert1')
>>> 
>>> n2 = hou.node('/shop/vopmaterial1/surface_output')
>>> n2.setInput(4, n1, 2)
>>> n2.setNamedInput('Cf', n1, 'clr')
>>> n1.inputNames()
('nN', 'nI', 'Kd', 'diff', 'facefwd')
>>> n2.setNamedInput('Cf', n1, 1
```
**Expressions**

Create a platonic sop in obj context, then change form Hscript to python in the current sop panel.

in Ry channel
```python
x = hou.ch('../null1/tx')*20
y = float(hou.expandString('$F'))
z = hou.pwd().outputs()[0].parm('ty').eval()*10
return x+y
```


```sh
>>> o = hou.parm('/obj/platonic1/tx')
>>> o.setExpression('$F', language = hou.exprLanguage.Hscript)
>>> 
```

**Python session**

>Inside Python source editor

```python
x = hou.ch('../null1/tx')*20
y = float(hou.expandString('$F'))
z = hou.pwd().outputs()[0].parm('ty').eval()*10
return x+y
````

```python
def Test():
    print("Test") 
```
>Inside python shell
```py
hou.session.test()
```

```python
import hou

def Action():
    print("test")
```
>Add a button to the operator, then add a callbackscript

```python
hou.session.action()
``` 
**Scene Time**

```sh
>> hou.frame()
46.0
>>> hou.setFrame(55)
>>> hou.frame()
55.0
>>> hou.time
<function time at 0x000000003409BE48>
>>> hou.time()
2.25
>>> hou.setTime(1)
>>> hou.fps()
24.0
>>> 
>>> hou.setFps(25)
>>> hou.playbar
<module 'hou.playbar'>
>>> hou.playbar.playMode()
playMode.Loop
>>> hou.playbar.setPlayMode(hou.playMode.Once)
>>> hou.playbar.play
<bound method playbar.play of <module 'hou.playbar'>>
>>> hou.playbar.setRealTime(1)
>>>
>>> hou.playbar.setPlaybackRange(1, 180) 
>>> hou.hscript('tset `(1-1)/$FPS` `100/$FPS`')
('', '')
hou.hscript('tset `(%s-1)/$FPS` `%s/$FPS`' %(10, 20))
```


- [Python Scripting](https://www.sidefx.com/docs/houdini/hom/index.html)
- [HOM Coockbook](https://www.sidefx.com/docs/houdini/hom/cb/index.html)
- [hou package](https://www.sidefx.com/docs/houdini/hom/hou/index.html)

