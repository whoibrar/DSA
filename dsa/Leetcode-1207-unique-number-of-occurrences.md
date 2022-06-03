---
published : true

title : 
permalink : 
layout : note
excerpt : DSA Problem and Solution

alias : 
categories : problem
tags : 

questionLink : 
questionType : 

solvedDate : 2022-05-28 00:00:00 +0000
---

## Problem Statement

- Given an array of integers `arr`, return `true` if the number of occurrences of each value in the array is **unique**, or `false` otherwise.

### Example

```

Input: arr = [1,2,2,1,1,3]
Output: true
Explanation: The value 1 has 3 occurrences, 2 has 2 and 3 has 1. No two values have the same number of occurrences.

```

## Solution Approaches

### O(N) sO(N) - Using Map and Set

- Using map to make a get all the frequencies
- Using set to check if they are all unique

```cpp

bool uniqueOccurrences(vector<int>& arr) {
	unordered_map<int, int> m;
	unordered_set<int> s;

	// adding to map
	for (int i = 0; i < arr.size(); i++) {
		m[arr[i]] += 1;
	}

	// adding to set
	unordered_map<int, int>::iterator b = m.begin();
	while (b != m.end()) {
		s.insert(b->second);
		b++;
	}

	return m.size() == s.size();

}

```

```python

def uniqueOccurrences(self, arr: List[int]) -> bool:
	mydic={}
	for i in arr:
		mydic[i]=mydic.get(i,0)+1
	return len(mydic.keys())==len(set(mydic.values()))

```

---

Return to [[DSA-Problems]]

---
