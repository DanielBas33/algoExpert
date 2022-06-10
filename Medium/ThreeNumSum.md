# Three Number Sum

### Understanding the problem

Given a non-empty arrat of distinct integers and a target sum create a function that finds all the triplets that sum up to that target. The numbers in the triplets should be ordered in ascending order as well as the triplets themselves.

#

### Approach : pointers

To solve this problem we will use a very useful technique to solve array problems. We will start by sorting the input array. We will iterate through the sorted array selecting two pointers, left and right. The left pointer will be at the next position of our current iteration while the right one will be at the end of the array. Now we just sum these three values and compare with the target, if we find the target we add the three numbers to our array and move both pointers. (right one to the left and left one to the right). If we get less or more than the target we just move the corresponding pointer to try to make the sum work. (right pointer if we need a smaller number or left pointer if we want a bigger number). If the left pointer passes the right one we go to the next iteration.

We just iterate through the len of the array minus two as we need those other two values for the pointers.

### Implementation

```python
def threeNumberSum(array, targetSum):
    array.sort()
    triplets = []
    for i in range(len(array) - 2):
        left = i + 1
        right = len(array) - 1
        while left < right:
            currentSum = array[i] + array[left] + array[right]
            if currentSum == targetSum:
                triplets.append([array[i],array[left],array[right]])
                left += 1
                right -= 1
            elif currentSum > targetSum:
                right -= 1
            elif currentSum < targetSum:
                left += 1
            
    return triplets
```

### Complexity Analysis

- Time Complexity: O(N^2). We do sort which takes nlog(n) time but since we have the while loop inside the for loop we already get a bigger time complexity in N^2 which ends up being the final time complexity.

- Space Complexity: O(N). Because we do fill the new triplets array with integers from the array and in the worst cases this array will a number of integers in the order of N.

#
