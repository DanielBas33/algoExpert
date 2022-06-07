# Complexity Analysis, Memory and Big O Notation

## Complexity Analysis

Complexity can be divided into time and space complexity. Time complexity is what we use to measure how much time an algorithm will take to find a solution whereas space complexity measures the memory this algrithm or solution uses. Generally we look for solutions with the best complexities in general so when we say complexity analysis we mean to the process of finding each of the complexities for our different solutions to one problem.

NOTE: Different data structures have different time and space complexities for the same actions.

## Memory

A bit is the fundamental unit of information in Computer Science that represents a state with two possible values, 0 and 1.
A byte is a group of eight bits stored together to store more information, a single byte can store up to 256 different data values. This values are numbers represented in binary format, from 0 to 255.
To store numbers we usually talk about 32 or 64 bit integers. These just are groups of 4 or 8 bytes stored together. For strings we map each letter with a different number, using ASCII.
Pointers can be also stored in memory addreses. These are useful since they let us join to different memory adresses without them having to be back to back.
Memory basically is where we store information in a computer and understanding how it works is fundamental to calculate space complexity. Data is stored in bytes (bits), pointers are used to refer to data addresses from other addresses and accesing a byte or fixed number of bytes is considered an elementary operation, constant.

## Big O Notation

Instead of calculating the literal time or space complexity in ms or bytes we use different notations to measure these. Big O Notation tells us how much the algorithm time or space increases as the input increases. O(1) would be constant time or space which means the output is the same as the input increases. O(n) is linear time or space, the output increases linearly with the input. O(n^2) as we can imagine is even worse than the previous as the time or space grows much faster than the previous ones. There are more possible notations but the most common ones are: O(1), O(log(n)), O(n), O(nlog(n)), O(n^x), O(2^n), O(n!). To visualize these, we can use graphs to see the difference between them.
Usually in a problem for the same solution we can get multiple scenarios where the complexity can be worse or better. In this cases we tend to pick always the worse case.

NOTE: If an algorithm takes O(n + 1) we say the Big O Notation to be O(n) as the 1 is irrelevant whenever the n gets bigger. The same goes to O(n^2 + n), this would result in O(n^2).

