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

solvedDate : 2022-06-01 00:00:00 +0000
---

## Problem Statement

- Find the first non-repeating element in a given array **arr** of **N** integers.  
**Note:** Array consists of only positive and negative integers and **not zero**.

### Example

```

Input : arr[] = {-1, 2, -1, 3, 2}
Output : 3

Explanation:
-1 and 2 are repeating whereas 3 is 
the only number occuring once.
Hence, the output is 3. 

```

## Solution Approaches

### O(N) sO(N) Frequency Hash Map

- Using same approach as [[GFG-first-repeating-element]]

```cpp

int firstNonRepeating(int *arr, int n) {
	map<int, int> m;

	for (int i = 0; i < n; i++) {
		m[arr[i]]++;
	}

	for (int i = 0; i < n; i++) {
		if (m[arr[i]] == 1) {
			return i;
		}
	}

	return -1;
}

```

```python

def firstNonRepeating(self, arr, n): 
	mydic={}
	for i in arr:
		mydic[i]=mydic.get(i,0)+1
	for i in arr:
		if(mydic[i]==1): return i;
	return -1

```

---

Return to [[DSA-Problems]]

---
