# Closest Value BST

### Understanding the problem

Given a Binary Search Tree and an integer return the closest node to the integer in the BST.

A BST is a data structure with a tree form. Each node can have up to two children, right and left children. The right child's value has to be equal or bigger than the parent's value and the left child's value has to be equal or smaller. 

#

### Approach 1: recursion

The first approach that comes to mind is recursion. This tool works well to traverse through trees as we can just call the same time on the following nodes. We just have to store the current closest node and call the function on the right or left child depending on whether the target value is bigger or smaller than the current node. We stop when we get to the end of the tree and return the current closest variable.

### Implementation

```python
def findClosestValueInBst(tree, target):
	return auxfindClosestValueInBst(tree, target, tree.value)

def auxfindClosestValueInBst(tree, target, currentClosest):
	if tree is None:
		return currentClosest
	if abs(target - tree.value) < abs(target - currentClosest):
		currentClosest = tree.value
	if target < tree.value:
		return auxfindClosestValueInBst(tree.left, target, currentClosest)
	if target > tree.value:
		return auxfindClosestValueInBst(tree.right, target, currentClosest)
	else:
		return currentClosest
	
# This is the class of the input tree.
class BST:
    def __init__(self, value):
        self.value = value
        self.left = None
        self.right = None
```

### Complexity Analysis

- Time Complexity: O(N). Being a BST and given that we eliminate half of the nodes when going through the tree the AVG time will be O(log(n)) but the worst case will be still O(N) because we can get a tree with nodes that only have right childs and we would then have to traverse through N nodes.

- Space Complexity: O(N). Because of the call stack that we are filling each time we call the recursive function.

#

### Approach 2: iteratively

Knowing how to solve the problem with recursion we have to ask if we can improve either of the complexities. The answer is yes, the space complexity could be improved by using iteration instead of recursion for solving the problem. Having an initial node we can use a while loop to traverse through the nodes of the tree similarly to the recursive function.

NOTE: inside the while loop take care because one of the if conditions needs to be an elif. This is because if not the wrong value will be compared on the second one.

### Implementation

```python
def findClosestValueInBst(tree, target):
    currentClosest = tree.value
	currentNode = tree
	while currentNode is not None:
		if abs(target - currentNode.value) < abs(target - currentClosest):
			currentClosest = currentNode.value
		if target < currentNode.value:
			currentNode = currentNode.left
		elif target > currentNode.value:
			currentNode = currentNode.right
		else:
			break
    return currentClosest


# This is the class of the input tree.
class BST:
    def __init__(self, value):
        self.value = value
        self.left = None
        self.right = None

```

### Complexity Analysis

- Time Complexity: O(N). Being a BST and given that we eliminate half of the nodes when going through the tree the AVG time will be O(log(n)) but the worst case will be still O(N) because we can get a tree with nodes that only have right childs and we would then have to traverse through N nodes.

- Space Complexity: O(1). We do not use any extra space.

#
