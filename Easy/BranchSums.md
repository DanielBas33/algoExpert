# Branch Sums

### Understanding the problem

Given a Binary Search Tree return the sums of its different branchs from left to right.

A BST is a data structure with a tree form. Each node can have up to two children, right and left children. The right child's value has to be equal or bigger than the parent's value and the left child's value has to be equal or smaller. 

A branch sum is the sum of all the values from the nodes on a given branch.

#

### Approach : recursion

As this is a BST problem we can solve it using recursion. We will have a list of integers and a branchSum integer apart from the tree as inputs for our recursion function. On the actual function we check if we are on a leaf, if not we add the current node value to the branch sum and check if we are at the end of the branch. If we are we add the current branchSum to the list that we have. At the end we call the function on both child nodes. The final list of sums will be our answer.

### Implementation

```python
class BinaryTree:
    def __init__(self, value):
        self.value = value
        self.left = None
        self.right = None

def branchSums(root):
	sums = []
	branchSumsHelper(root, 0, sums)
    return sums

def branchSumsHelper(node, cumulativeSum, sums):
	
	if node == None:
		return 
	cumulativeSum += node.value
	if node.right == None and node.left == None :
		sums.append(cumulativeSum)
		return
	branchSumsHelper(node.left, cumulativeSum, sums)
	branchSumsHelper(node.right, cumulativeSum, sums)
```

### Complexity Analysis

- Time Complexity: O(N). Being a BST and given that we eliminate half of the nodes when going through the tree the AVG time will be O(log(n)) but the worst case will be still O(N) because we can get a tree with nodes that only have right childs and we would then have to traverse through N nodes.

- Space Complexity: O(N). Because of the call stack that we are filling each time we call the recursive function.

#
