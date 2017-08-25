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

> Create a groupStackNode and rename the node
{% highlight python %}
root = NodegraphAPI.GetRootNode()
myNode = NodegraphAPI.CreateNode("GroupStack", root)
{% endhighlight %}
---




