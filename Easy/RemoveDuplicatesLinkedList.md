# Remove Duplicates From Linked List

### Understanding the problem

Given the head of a Singly Linked LIst whose nodes are in sorted order with respect to their values. Write a function that returns a modified version of the Linked List that doesn't contain any nodes with duplicate values. The returned Linked List should be the same one, not new and also should be sorted.
Each node on the List has an integer value as well as a next node pointing to the next node on the list or None if its the tail.

#

### Approach 

This is a simple question to learn to iterate through a linked list. We can use a while loop to iterate through the linked list until currentNode is equal to None. Also inside we will compare currentNode with the next node and this next node will keep going to the next one until it is a different one from which that node will be the new currentNode. When we reach the null or None node at the end we just return the LinkedList.

### Implementation

```python
class LinkedList:
    def __init__(self, value):
        self.value = value
        self.next = None

def removeDuplicatesFromLinkedList(linkedList):
	currentNode = linkedList
	nextDistinct = linkedList.next
	
	while currentNode != None:
		while nextDistinct != None and nextDistinct.value == currentNode.value:
			nextDistinct = nextDistinct.next
		currentNode.next = nextDistinct
		currentNode = nextDistinct
		
    return linkedList
```

### Complexity Analysis

- Time Complexity: O(N), where n is the number of nodes in the list.

- Space Complexity: O(1), as asked by the prompt we do not use any extra space.

#
