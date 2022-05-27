# Run Length Encoding

### Understanding the problem

Given a non-empty string, return its run-length encoding. 

Run-length encoding is a form of data compression in which data is stored by grouping identical characters from the original string.

Ex: "AAA" -> "3A" 

The maximum grouping will be 9 since the data must be decodable so:

"AAAAAAAAAAAA" is not 12A but 9A3A

#

### Approach

To solve the problem we will need to store values in an array and iterate through the input string. For each iteration we will compare the current and previous characters and check if they are the same. At the same time store a count of the number of identical characters and sum 1 for each iteration. If we find a different character or the count gets to 9 we just start again the counter.

Note: if you compare current with previous char, you will need to start with i = 1. This means the last character in the string will not be iterated through so we need to handle this last char after the for loop.

### Implementation

```python
def runLengthEncoding(string):
    runLength = []
    currentLength = 1
    for i in range(1, len(string)):
        currentChar = string[i]
        previousChar = string[i-1]
        if currentChar != previousChar or currentLength == 9:
            runLength.append(str(currentLength))
            runLength.append(previousChar)
            currentLength = 0
        currentLength += 1

    # Handle last run
    runLength.append(str(currentLength))
    runLength.append(string[len(string) - 1])
    return "".join(runLength)
```

### Complexity Analysis

- Time Complexity: O(n). Where n is the number of letters in the string.

- Space Complexity: O(n). Where n is the number of letters in the string.

#

