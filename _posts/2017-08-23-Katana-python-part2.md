---
layout: post
title: Katana Memo 
tags: [katana, python]
categories:
- blog
---

> get the full list of al available node types
{% highlight python %}
nodetypes = NodegraphAPI.GetNodeTypes()
nodetypes.sort()
for nodetype in nodetypes:
    print(nodetype)
{% endhighlight %}
---

> Get help on packages
{% highlight python %}
help(NodegraphAPI)
help(Nodes3DAPI)
help(UI4)
help(UI4.Util)
{% endhighlight %}
---

> Get help on classGroupStackNode in module
{% highlight python %}
NodegraphAPI.GroupStack
help(NodegraphAPI.GroupStack.GroupStackNode)
{% endhighlight %}
---

> Create a new GroupStack node at root location and rename it
{% highlight python %}
root = NodegraphAPI.GetRootNode()
my_node = NodegraphAPI.CreateNode('GroupStack', root)
#rename the node
my_node.setName('my_stackGS')
{% endhighlight %}
---

> Create a new prmanObjectStatement node rename it and stack in my_stackGS (created above)
{% highlight python %}
#create node
my_prman = NodegraphAPI.CreateNode('PrmanObjectStatements', root)
#rename the node
my_prman.setName('prman_OS')
#put node in groupstack
my_node.buildChildNode(my_prman)
#check the child node available
my_node.getChildren()
{% endhighlight %}
---

> Adjusting attributes using script (may not work)
{% highlight python %}
root = NodegraphAPI.GetRootNode()
my_prman = NodegraphAPI.CreateNode('PrmanGlobalStatement', root)
en = my_prman.getParameter('args.prmanGlobalStatement.pixelVariance.enable')
#enable assignement to True
en.setValue(1,0)
#Set pixel variance value to 2 at frame 0
val = my_prman.getParameter('args.prmanGlobalStatements.pixelVariance.value')
val.setValue(2,0)
{% endhighlight %}
---

> If the PrmanGlobalStatements alredy exist : 
{% highlight python %}
#get the node 'PrmanGlobalStatement' and store it in my_prman
myprman = NodeGraphAPI.GetNode('PrmanGlobalStatement')
#editing of the value is the same as above
{% endhighlight %}
---

> Select Nodes and run this to get a list of selected nodes
{% highlight python %}
sel = NodegraphAPI.GetAllSelectedNodes()
print(sel)
{% endhighlight %}
---

> Create a prmanGlobalStatement and use this to get child parameters of the node
{% highlight python %}
sel = NodegraphAPI.GetNode('PrmanGlobalStatements')
for p in sel.getParameters().getChildren():
    print(p)
{% endhighlight %}
---

> Delete nodes
{% highlight python %}
sel = NodegraphAPI.GetNode('PrmanGlobalStatements')
sel.delete()
{% endhighlight %}
---

> Get list of locations
{% highlight python %}
list = ScenegraphManager.getActiveScenegraph().getSelectedLocations()
print(list)
{% endhighlight %}
---





