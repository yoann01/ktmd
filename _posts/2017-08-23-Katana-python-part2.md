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
{% endhighlight %}
---

> Get help on classGroupStackNode in module
{% highlight python %}
 NodegrapAPI.groupStack
 help(NodegraphAPI.groupStack.GroupStackNode)
{% endhighlight %}
---

> Create a new GroupStack node at root location and rename it
{% highlight python %}
root = NodegraphAPI.GetRootNode()
my_node = NodegraphAPI.CreateNode('GroupStack', root)
#rename the node
myNode.setName('my_stackGS')
{% endhighlight %}
---

> Create a new prmanObjectStatement node rename it and stack in my_stackGS
{% highlight python %}
#create node
my_prman = NodegraphAPI.CreateNode('PrmanObjectStatment', root)

#rename the node
my_prman.setName('prman_OS')

#put node in groupstack

#check the child node available
{% endhighlight %}

---


