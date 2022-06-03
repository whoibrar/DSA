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

- Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.
- You may assume that each input would have exactly one solution, and you may not use the same element twice.
- You can return the answer in any order.

### Example

```

Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].

```

## Solution Approaches

### O(N) sO(N) - Using Maps or Dictionary

- For every `val` in `nums` check if `target-val` is already present in `hashmap`
	- If present just return the index of those
	- If not present, add to hasmap

```cpp

vector<int> twoSum(vector<int>& nums, int target) {
	
	unordered_map<int, int> m;
	vector<int> ans;

	for (int i = 0; i < nums.size(); i++) {
		int remain = target - nums[i];

		if (m.find(remain) != m.end()) {
			ans.push_back(m[remain] + 1);
			ans.push_back(i + 1);
			return ans;
		}
		m[nums[i]] = i;
	}
	return ans;

}

```

```python

def twoSum(self, nums, target):
	hm={}
	for pos,val in enumerate(nums):
		if target-val in hm:
			return [hm[target-val],pos]
		hm[val]=pos

```

### O(N^2) sO(1) - Recursively Searching

```python

def twoSum(self, nums, target):
	for x in range(len(nums)):
		if target-nums[x] in nums and x!=nums.index(target-nums[x]):
			return [x,nums.index(target-nums[x])]

```

### O(LogN) sO(N) - Store Index Sort Array Two Pointers

```python

def twoSum(self, nums, target):
	
	ar=[] 
	# store the [idx,val]
	for (x,y) in enumerate(nums):
		ar.append([x,y])
	
	# sort wrt [idx,val][1] aka val
	ar.sort(key=lambda x: x[1])
	
	# simple two pointer sum check
	l,r=0,len(nums)-1
	while l<r:
		if ar[l][1]+ar[r][1]==target:
			return [ar[l][0],ar[r][0]]
		elif ar[l][1]+ar[r][1]<target:
			l+=1
		else:
			r-=1

```

---

Return to [[DSA-Problems]]

---
