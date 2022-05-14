# Minimum Waiting Time

## Understanding the problem

Given a non-empty array of positive integers representing the amounts of time specific queries take to execute. Return the minimum total waiting time for each array.
Queries are executed one at a time and the waiting time of a query is the time the ones before it took to execute. The total waiting time is the sum of these waiting times for every query.

ex: [1,4,5] is going to return a smaller waiting time than [5,4,1]

For the array [3,2,1,2,6] the minimum waiting time is 17. That is if we transform it into [1,2,2,3,6]

## Approach

As we saw on the different examples there is a pattern, we want to order the array from smallest to largest. This is obvious as we are going to be adding up the previous waiting times again and again so the smaller the first ones the better. For this approach we will use a sorting function to sort the array and then we will use a for loop to traverse through it. During this loop we will keep track of two variables, the currentSum that we have and the subTotal which consists of the sum of numbers up to the current iteration. On each iteration we will add up the subTotal and the current number to the currentSum. The returning value will be this currentSum.

### Implementation

```python
def minimumWaitingTime(queries):
 queries.sort()
 subtotal = 0
 sum = 0
 for number in queries[:-1]:
  sum += number + subtotal
  subtotal += number
 return sum
```

### Complexity Analysis

- Time Complexity: O(nlog(n)). We sorted the query.

- Space Complexity: O(1). No additional space used.
