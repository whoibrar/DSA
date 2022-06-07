---
published : true

title : 
permalink : 
layout : note
excerpt : DSA Problem and Solution

alias : 
categories : problem
tags : 

questionLink : "https://leetcode.com/problems/single-element-in-a-sorted-array/"
questionType : 

solvedDate : 2022-05-16 00:00:00 +0000
---

## Problem Statement

- Given a sorted array consisting of only integers where every element appears exactly twice, except for one element which appears exactly once.
- Find that one element

### Example

```
given [1,1,2,3,3,4,4,8,8]
return 2

as it appears only once
```

## Solution Approaches

### O(N) - Bit Manipulation

- We know that `0^x=x` and `x^x=0` using [[Bit Manipulation]]
- So on applying xor on all elements of array, duplicates will cancel each other out.
- We are left with the element that occurs only once.

```cpp

int singleNonDuplicate(vector<int>& nums) {
	int x = 0;
	for(int i=0;i<nums.size();i++){
		x^=nums[i];
	}
	return x;

```

### Other Approaches

- [✅ [C++/Python] 7 Simple Solutions w/ Explanation | Brute + Hashmap + XOR + Linear +2 Binary Search - LeetCode Discuss](https://leetcode.com/problems/single-element-in-a-sorted-array/discuss/1587270/C%2B%2BPython-7-Simple-Solutions-w-Explanation-or-Brute-%2B-Hashmap-%2B-XOR-%2B-Linear-%2B2-Binary-Search)

## Related

---

Return to [[DSA-Problems|DSA Problems]]

---
