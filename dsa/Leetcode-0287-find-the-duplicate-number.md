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

solvedDate : 2022-05-17 00:00:00 +0000
---

## Problem Statement

- Given an array of integers `nums` containing `n + 1` integers where each integer is in the range `[1, n]` inclusive.
- There is only **one repeated number** in `nums`, return _this repeated number_.

### Example

```

Input: nums = [1,3,4,2,2]
Output: 2

```

## Solution Approaches

### O(N^2) - Brute Force also [[py.oneliners|Python OneLiner]]

- For every Element of given array check its frequency 

```python 

def findDuplicates(nums):
	# O(n^2) 
	return [x for x in nums if nums.count(x)>1][0]

```

### O(N) - Using Hash-Map to store frequency  

- Create a Hash-map. 
- Iterate through array and update the values in HM.
- Iterate again to find the element where frequency is unusual.

```cpp

int findDuplicate(vector<int>& v) {
	int n = v.size();

	unordered_map<int, int> hm;

	for (int i = 0; i < n; i++) {
		hm[v[i]] += 1;
	}

	for (int i = 0; i < n; i++) {
		if (hm[v[i]] > 1) return v[i];
	}

}

```

---

Return to [[DSA-Problems]]

---
