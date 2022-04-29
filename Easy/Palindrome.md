# Palindrome Check

### Understanding the problem

Given a string, I am asked to write a function that checkes if the string is a Palindrome or not. Return true if it is and false if it is not. A palindrome is a string that is equal when read from left to right or right to left. 

Example: abcdcba 

#


### Approach 1 : Create String (iteration)

The first obvious approach is to create a reversed string of the given string and compare them.

### Implementation

```python
def isPalindrome(string):
    reversedString = ""
    for i in reversed(range(len(string))):
        reversedString += string[i]
    return reversedString == string
```

### Complexity Analysis

- Time Complexity: O(N^2). This is because when creating our new string we are actually creating a new string each time we add a character. This is how string concatenation works in most languages like python.

- Space Complexity: O(N). Because we are creating a string of N characters where N is the length of the input string.

#

### Approach 2 : Create Array (iteration)

The second obvious approach, knowing that string concatenation makes our time complexity worse, is to create an array instead of a string.

### Implementation

```python
def isPalindrome(string):
    reversedChars = []
	for i in reversed(range(len(string))):
		reversedChars.append(string[i]) 
    return string == "".join(reversedChars) 
```

### Complexity Analysis

- Time Complexity: O(N). Appending values to a list or array is a constant time operation which makes the time complexity O(N).

- Space Complexity: O(N). Because we are creating an array of N characters where N is the length of the input string.

#

### Approach 3 : Recursion

In this approach we will use recursion properties to solve the problem. We could create a function that checks if the first and last characters are equal and then calls itself on the characters in the middle.

### Implementation

```python
def isPalindrome(string, i=0):
    j = len(string) - 1 - i
    return True if i >=j else string[i] == string[j] and isPalindrome(string, i + 1)
```

### Complexity Analysis

- Time Complexity: O(N). Really its O(N/2) but at the end thats the same as O(N).

- Space Complexity: O(N). It is not O(1) because we have to store the state of the function for each loop in the call stack.

Note: There is something called tail recursion where if the recursion is called at the end of the function instead of storing more information on the stack it replaces it. This would technically make the space complexity O(1). Some compilers even do this by default and modify your function so that it is tail recursive.

#

### Approach 4 : Iteration with pointers

We can start iterating the string with a pointer at the start and a pointer at the end and keep iterating the two pointers until they are not the same character `False` or they are in the same position `True`.

### Implementation

```python
def isPalindrome(string):
    leftIdx = 0
	rightIdx = len(string) - 1
	while leftIdx < rightIdx:
		if string[leftIdx] != string[rightIdx]:
			return False
		leftIdx += 1
		rightIdx -= 1
    return True
```

### Complexity Analysis

- Time Complexity: O(N). We are still iterating through the string.

- Space Complexity: O(1). Pointers are constant space and we do not use other strings.

#
