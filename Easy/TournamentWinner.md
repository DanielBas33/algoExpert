# Tournament Winner

### Understanding the problem

Given two non-empty arrays, one representing matches between different teams and one representing the results return the winner of the tournament. The arrays are of the form:

Competions =[[TEAM-A,TEAM-B],[TEAM-B,TEAM-C]] Results =[0,1]. 0 in the results means the home team(first team) won and 1 means the away team won. On this example TEAM A wins the first match and TEAM C wins the second one.

#

### Approach 
In this approach we will store the points each team has as well as the current winner. At the end we will output this current winner variable. On each iteration of the given arrays we will check what team won from the competitions array using the results array. We will use a hash table to store the information, checking if the winner is already there and either adding 3 to its current store if it is there or creating a new entry for that team with an initial score of 3. After storing in the hash table we compare the score for that team with our currentWinner and if the new team has a bigger score we swap them. For this to work we will initalize an empty string with a score of 0 for the first comparations. 


### Implementation

```python
def tournamentWinner(competitions, results):
    points = {}
	currentWinner = ''
	points[""] = 0
	for i in range (len(competitions)):
		if results[i] == 0:
			result = 1
		else:
			result = 0
		winner = competitions[i][result]
		if winner in points :
			points[winner] += 3
		else:
			points[winner] = 3
			
		if points[currentWinner] < points[winner]:
			currentWinner = winner
		
    return currentWinner
```

### Complexity Analysis

- Time Complexity: O(N), where N is the number of competitions.

- Space Complexity: O(K), where K is the number of teams.

#
