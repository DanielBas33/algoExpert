# First Non-Repeating Character 

### Understanding the problem

Given a string of lowercase English-alphabet letters, write a function that returns the index of the first non-repeating character.

Example: `abcdcaf` would return 1 because b is the first not repeated character.

NOTE: if there are no characters that do not repeat return -1.

#

### Approach 1 

For the first approach that comes to mind we could just loop through the string and for every character loop again (a for inside of the first for). We could then determine one character at a time if it repeats itself and return its index if it does not. The problem with this approach is the time complexity we get, O(n^2) as we loop inside of a loop.

### Implementation

```python
def firstNonRepeatingCharacter(string):
    for idx in range(len(string)):
        foundDuplicate = False
        for idx2 in range(len(string)):
            if string[idx] == string[idx2] and idx != idx2:
                foundDuplicate = True
        if not foundDuplicate:
            return idx
    return -1
```

### Complexity Analysis

- Time Complexity: O(n^2), where n is the length of the given string.

- Space Complexity: O(1).

#

### Approach 2

For the second approach we will use a hash table to store frequencies of the different characters. We use a loop to store these on the hash table and a second loop to search for characters with only a 1 as a value. If we find them we just return the index of the character, if not we return -1 at the end. This solution uses too two loops but the second one goes outside of the first one which makes a time complexity of O(2n) or O(n) which is much better.

NOTE: Space complexity stays as O(1) because on the problem promt we got told that the string would only have lowercase english letters. This means it can only have 26 characters in it which means constant space.

### Implementation

```python
def firstNonRepeatingCharacter(string):
    chars = {}
    for character in string:
        if character not in chars:
            chars[character] = 0
        chars[character] += 1
    for character in string:
        if chars[character] == 1:
            return string.index(character)
    return -1
```

### Complexity Analysis

- Time Complexity: O(2n) = O(n), where n is the length of the given string.

- Space Complexity: O(1). Because of 26 max size of the hash table.

#
