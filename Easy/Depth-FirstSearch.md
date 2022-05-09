# Depth-First Search

### Understanding the problem

Given a Node class that has a name and an array of children which form a graph with an acyclic tree-like structure we are asked to implement depth first search to store all of the nodes of the tree in an array.

Depth first search basically traverses the tree by focusing on each branch at a time instead of going through each node children which would be breadth first search. 

#

### Approach: recursion

For this problem we can use recursion as we want to do the same thing over the different nodes on the tree. Our recursive function will append the name of the current node to the array and then call itself on the children of that node. As we will be calling the function using a for loop the second child (if there is one) will have to wait for the recursive function to come back.


### Implementation

```python
class Node:
    def __init__(self, name):
        self.children = []
        self.name = name

    def addChild(self, name):
        self.children.append(Node(name))
        return self

    def depthFirstSearch(self, array):
		array.append(self.name)
		for node in self.children:
			node.depthFirstSearch(array)
        
		return array
```

### Complexity Analysis

With graphs time and space complexities are a bit more complex as we have both Vertices V and Edges E to consider. Vertices are the actual nodes with values whereas edges are the connections between these vertices.

- Time Complexity: O(V + E). We have to traverse every node so we traverse every vertex. But also we called a for loop on each of these nodes, this for loop has a length equal to the number of edges that particular node has. This makes it so that the time complexity is v + e.

- Space Complexity: O(V). Because of the call stack or the actual array we are using.

#