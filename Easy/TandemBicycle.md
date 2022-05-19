# Tandem Bicycle

### Understanding the problem

A tandem bicycle is a two person bicycle where the speed is dictated by the fastest pedaling one. 

Given two arrays of the red and blue shirted people speeds I am asked to return the fastest or slowest combination of red and blue shirts. Return fastest or slowest combination depending on a boolean, if true fastest and if false slowest. 

#

### Approach 
This is another great example of a problem where we can quickly solve it by sorting the arrays. If we sort both arrays and join the numbers in order we will get the slowest solution whereas if we sort one and reverse sort the other one we will get the fastest solution. This is because for the fastest solution we wont faster people to match slower ones and the opposite for the slowest solution.

### Implementation

```python
def tandemBicycle(redShirtSpeeds, blueShirtSpeeds, fastest):
	redShirtSpeeds.sort()
	if fastest:
		blueShirtSpeeds.sort(reverse = True)
	else:
		blueShirtSpeeds.sort()
	speedTotal = 0
	for idx in range(len(redShirtSpeeds)):
			speedTotal += max(redShirtSpeeds[idx],blueShirtSpeeds[idx])
			
    return speedTotal
```

### Complexity Analysis

- Time Complexity: O(nlog(n)), because you need to sort the arrays.

- Space Complexity: O(1).

#
