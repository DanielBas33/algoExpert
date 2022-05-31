# Generate Document

### Understanding the problem

Given a string of available characters and a string representing a document, write a function that determines if you can generate the given document with the available characters in the string. 

NOTE: The number of required characters of one type must be equal or superior, you cannot reuse a given character. This also is for special characters like spaces. 

Example: `aabbcc` can generate `abcabc` but `abbcc` cannot.

#

### Approach 1 

To solve the problem we need to now the frecuency required for each character in the problem and then compare it with the available frecuency for each character on the given string. We could just loop the document and for each character calculate the frecuency, search for that character in the string and return also its frecuency. Return False if the first frecuency is bigger than the second one or else just continue and return True at the end.

Although this solution works it is obvious that the time complexity is not going to be amazing as we are looping inside the initial loop. 

### Implementation

```python
def generateDocument(characters, document):
    for character in document:
        documentFrequency = countCharacterFrequency(character, document)
        charactersFrequency = countCharacterFrequency(character, characters)
        if documentFrequency > charactersFrequency:
            return False
    return True

def countCharacterFrequency(char, string):
    frequency = 0
    for character in string:
        if character == char:
            frequency += 1
    return frequency
```

### Complexity Analysis

- Time Complexity: O(m * (n + m)), where n is the length of the given string and m the length of the document.

- Space Complexity: O(1).

#

### Approach 2

For the second approach we could just use the first one and add a list of already counted characters where we can store characters which we have already compared. This new solution will still have a bad time complexity but at least instead of multiplying the document length we would multiply the length of the newly created list which basically is the number of different characters in the document.

Instead of that we will come up with a different solution. We will use hash tables to solve the problem. To make this work we will loop through the string creating a hash table where characters will be the key and the frequency will be the value. We can the just loop through the document and substract 1 from the value for each character found on the document. If during this process any value is smaller than 0 or we dont find a given character in the hash table we return False, else we return True.
With this new solution we have a much better time complexity but our space complexity gets worse as we have to create this new hash table.

### Implementation

```python
def generateDocument(characters, document):
    chars = {}
    for char in characters:
        if char not in chars:
            chars[char] = 0
        chars[char] += 1
    for character in document:
        if character not in chars or chars[character] <= 0:
            return False
        chars[character] -= 1
    return True
```

### Complexity Analysis

- Time Complexity: O(n + m), where n is the length of the given string and m the length of the document.

- Space Complexity: O(c). Where c is the number of unique characters in the given string.

#
