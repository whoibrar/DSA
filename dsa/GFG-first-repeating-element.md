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

solvedDate : 2022-05-31 00:00:00 +0000
---

## Problem Statement

- Given an array arr[] of size n, find the first repeating element. The element should occurs more than once and the index of its first occurrence should be the smallest.
- It has 1-based Indexing

### Example

```

Input:
n = 7
arr[] = {1, 5, 3, 4, 3, 5, 6}

Output: 2

Explanation: 
5 is appearing twice and 
its first appearence is at index 2 
which is less than 3 whose first 
occuring index is 3.

```

## Solution Approaches

### O(N) sO(N) Using Frequency HashMap

- Create a frequency map of given array.
- Iterate through array again and return the first element who's frequency is more than one

```cpp

int firstrepeated(int *arr, int n) {
	map<int, int> m;

	for (int i = 0; i < n; i++) {
		m[arr[i]]++;
	}

	for (int i = 0; i < n; i++) {
		if (m[arr[i]] > 1) {
			return i + 1;
		}
	}

	return -1;
}

```

```python

def firstRepeated(self,arr, n):
	mydic={}
	for x in arr:
		mydic[x]=mydic.get(x,0)+1
	for i in range(len(arr)):
		if(mydic[arr[i]]>1):
			return i+1
	return -1

```


---

Return to [[DSA-Problems]]

---
