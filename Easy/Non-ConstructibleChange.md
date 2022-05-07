# Non-Constructible Change

### Understanding the problem

Given an array of positive integers representing the value of coins, we are asked to create a function that returns the minimum amount of change that we cannot generate. 

Ex: [1,2,5] would return 4 because we can generate 1,2 and 3 but we cannot generate a change of 4.
#

### Approach 

To solve this question we will be taking advantage of sorting, the first thing we will do to solve it is to apply any sorting function over the given array. Now that we have a sorted array of positive integers we can start at the beginning of the array. At first the max change we have is 0 because we did not iterate through any coins. For the first iteration we are looking for our current change + 1. If we find a value larger than our change + 1 then we finish and our change + 1 is the result. On the other hand if we find something smaller than our change + 1 we add this coin to our current max change. If we iterate through every coin then we just return our change + 1. I will give an example to make this more clear.

Initial given array: [1,2,3,5,13]

First iteration: CurrentChange = 0  Coin = 1 | CurrentChange + 1 = 1 | Here the coin is equal or smaller than the currentChange + 1 so we add the coin to our current change

Second iteration: CurrentChange = 1 Coin = 2 | CurrentChange + 1 = 2 | Again the coin is equal or smaller than the currentChange + 1

Third iteration: CurrentChange = 3 Coin = 3 | CurrentChange + 1 = 4 | Same as before we add the coin to our currentChange

Fourth iteration: CurrentChange = 6 Coin = 5 | CurrentChange + 1 = 7 | The coin is still smaller 

Up to now we can make 11 in change, 12 is our next objective. If we get a coin equal or smaller than 12 then we could make change up to 23 but if we get a larger one then we can never sum up to 12 which is the case.

Fifth iteration: CurrentChange = 11 Coin = 13 | CurrentChange + 1 = 12 | The coin is bigger than our change + 1 -> Return CurrentChange + 1

### Implementation

```python
def nonConstructibleChange(coins):
    coins.sort()
	currentMaxChange = 0
	for coin in coins:
		if coin > currentMaxChange + 1:
			return currentMaxChange + 1
		currentMaxChange += coin
    return currentMaxChange + 1
```

### Complexity Analysis

- Time Complexity: O(nlog(n)), because of the sorting.

- Space Complexity: O(1).

#
