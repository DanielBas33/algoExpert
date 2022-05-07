# Node Depths

### Understanding the problem

Given a Binary Search Tree return the sum of the depths of its nodes.

A BST is a data structure with a tree form. Each node can have up to two children, right and left children. The right child's value has to be equal or bigger than the parent's value and the left child's value has to be equal or smaller. 

A node depth is the distance between itself and the root of the BST.

ex: The rooot has a depth of 0 and each of its childs has a depth of 1.

#

### Approach: recursion

The first approach that comes to mind is recursion. This tool works well to traverse through trees as we can just call the same time on the following nodes. this recursive function will recieve a node and the currentSum and it will call that nodes childs adding 1 to currentSum for every layer. This will end with the trees leafs which will return 0.

### Implementation

```python
def nodeDepths(root):
    return nodeDepthsHelper(root,0)

def nodeDepthsHelper(node,currentSum):
	if node is None:
		return 0
	return currentSum + nodeDepthsHelper(node.left, currentSum + 1) + nodeDepthsHelper(node.right, currentSum + 1)

# This is the class of the input binary tree.
class BinaryTree:
    def __init__(self, value):
        self.value = value
        self.left = None
        self.right = None
```

### Complexity Analysis

- Time Complexity: O(N). We have to reach every node for this problem.

- Space Complexity: O(h). Because of the call stack that we are filling each time we call the recursive function. H is the height of the tree.

#