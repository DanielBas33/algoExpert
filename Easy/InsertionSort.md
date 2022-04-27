# Insertion Sort

### Understanding the problem

Given an array of integers, I am asked to write a function that uses Insertion Sort algorithm to sort the array and returns it.

#


### Approach : Iterative

The insertion sort is one of many sorting algorithms and although it is not the most eficient it does the job and it is easy to understand and implement. To implement it we will create a space at the begening of the array which will be our sorted array. Then we will iterate through the array and we will insert each element this new soretd array.

Example:

Starting point: unsorted

array = `[8,5,2,9,5,6,3]`

Step 1: `[5,8]` is sorted

array = `[5,8,2,9,5,6,3]`

Step 2: `[2,5,8]` is sorted

array = `[2,5,8,9,5,6,3]`

Step 3: `[2,5,8,9]` is sorted

array = `[2,5,8,9,5,6,3]`

...

Final array: sorted

array = `[2,3,5,5,6,8,9]`

On each iteration we insert one element to our sorted array until every element is sorted.


### Implementation

```python
def insertionSort(array):
    for i in range(len(array))
        j = i
        while j > 0 and array[j] < array[j-1]
            swap(j, j-1, array)
            j -= 1
	return array

def swap(i, j, array):
    array[i], array[j] = array[j], array[i]
```

### Complexity Analysis

- Time Complexity: O($$N^2$$), where N is the number of integers in the input array.

- Space Complexity: O(1). We use the same array that we were given by just swaping some numbers.

#