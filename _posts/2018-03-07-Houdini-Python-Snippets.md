---
layout: post
title:  Houdini Python
tags: [Houdini, Python]
categories:
- blog
---

```
HOM houdini object model
shelfTools 
Expressions
Pipeline
PythonSOP
New Operator Type
Assets
Callbacks
Houdini UI
Python Panel 
SOHO
pre\post render script
Mantra Filter
```

## HOM

### **Overview**

The Houdini Object Model (HOM) is an application programming interface (API) that lets you get information from and control Houdini using the **Python scripting language**. 

HOM replaces the functionality of Houdini’s previous scripting solutions, the **expression language** and **HScript**.


Open the python shell, create a geo sop.
in the shell:
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



- [Python Scripting](https://www.sidefx.com/docs/houdini/hom/index.html)
- [HOM Coockbook](https://www.sidefx.com/docs/houdini/hom/cb/index.html)
- [hou package](https://www.sidefx.com/docs/houdini/hom/hou/index.html)
