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
    print(node)
    
{% endhighlight %}
---

> Get help on packages
{% highlight python %}
 help(NodegrapfAPI)
 help(Nodes3DAPI)
 help(UI4)
{% endhighlight %}
---

> Get help on classGroupStacjNode in module
{% highlight python %}
 NodegrapAPI.groupStack
 help(NodegrapAPI.groupStack.GroupStackNode)
{% endhighlight %}
---

> Create a groupStackNode and rename the node
{% highlight python %}
root = NodegraphAPI.GetRootNode()
myNode = nodegraphAPI.CreateNode("GroupStack", root)
{% endhighlight %}
---



 honeyysharma [Github](https://github.com/honeyysharma/Katana)
