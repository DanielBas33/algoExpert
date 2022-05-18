# Class Photos

### Understanding the problem

You are a photographer and you have to take a picture to a class where half of the students are wearing red and the other half is wearing blue shirts. You need to create two rows with the same number of students but all red students must be on the same row and all the blue students have to be on the same row. Also taller students must be at the back.

You're given two arrays, one with the heights of blue students and the other one with the heights of red styudents. You are asked to return true or false if the conditions reached with those arrays.

#

### Approach 
This approach should be pretty strait forward, if we sort both arrays we just need to get the largest of the smallest students and then compare the rest. This means we compare red[0] with blue[0] after sorting and if red is the largest we need every positions on the sorted arrays to be larger for the red array than the blue, and the same if its the blue student the largest. This approach will have a time complexity of nlog(n) as we need to sort the arrays and a space complexity of 1 as we do not store anything extra.


### Implementation

```python
def classPhotos(redShirtHeights, blueShirtHeights):
	redShirtHeights.sort()
	blueShirtHeights.sort()
	
	if redShirtHeights[0] >= blueShirtHeights[0]:
	
		for idx, student in enumerate(redShirtHeights):
			if(student <= blueShirtHeights[idx]):
				return False
	else:
		for idx, student in enumerate(blueShirtHeights):
			if(student <= redShirtHeights[idx]):
				return False
	
    return True
```

### Complexity Analysis

- Time Complexity: O(nlog(n)), because you need to sort the arrays.

- Space Complexity: O(1).

#
