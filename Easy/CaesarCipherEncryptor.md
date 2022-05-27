# Caesar Cipher Encryptor

### Understanding the problem

Given a string of lowercase letters and a positive integer, write a function that returns the result of shifting those letters in the alphabet the amount indicated by the integer.

#

### Approach 1: Unicode

To solve this problem we can create a new array were we will be storing the new values for each letter. We will loop through the string calling the shift function on each letter and storing the value on the array. After this we can attach the array to a string and return that as the result.

There are two ways of solving the swaping values part of the problem, the first one is by using unicode functions. Usually in programming languages we have built in unicode functions that basically relate characters to a certain number. Having this we could just add the key to this number and transform back to letter. The only issue with this is that for example if z is 122 and we sum 2 we will get 124 but we want to return b which would be 98. To solve this we will use mod of 122 so that we always return the correct value.

Note: There is a case where the key is bigger than 26, so to be certain that our solution is always correct we can mod the key to 26.

### Implementation

```python
def caesarCipherEncryptor(string, key):
    newLetters = []
    newKey = key % 26
    for letter in string:
        newLetters.append(getNewLetter(letter, newKey))
    return "".join(newLetters)

def getNewLetter(letter, key):
    newLetterCode = ord(letter) + key
    return chr(newLetterCode) if newLetterCode <= 122 else chr(96 + newLetterCode % 122)
```

### Complexity Analysis

- Time Complexity: O(n). Where n is the number of letters in the string.

- Space Complexity: O(n). Where n is the number of letters in the string.

#

### Approach 2: Alphabet list

The second one, if we are not confortable with unicode functions, is to just create a list of all the letters in the alphabet and use the index of each one as the unicode value. So we will end up with a list of 26 values and we will use a similar approach where the key will be mod 26 to make sure and the sum of the key and the current index will also be mod 26. This approach is similar to the previous one but without using already existing functions.

### Implementation

```python
def caesarCipherEncryptor(string, key):
    newLetters = []
    newKey = key % 26
    alphabet = list("abcdefghijklmnopqrstuvwxyz")
    for letter in string:
        newLetters.append(getNewLetter(letter, newKey, alphabet))
    return "".join(newLetters)

def getNewLetter(letter, key, alphabet):
    newLetterCode = alphabet.index(letter) + key
    return alphabet[newLetterCode] if newLetterCode <= 25 else alphabet[newLetterCode % 26]
```

### Complexity Analysis

- Time Complexity: O(n). Where n is the number of letters in the string.

- Space Complexity: O(n). Where n is the number of letters in the string.

#