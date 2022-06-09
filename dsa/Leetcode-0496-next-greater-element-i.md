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

solvedDate : 2022-06-09 10:55:21 +0530

created_at: 2022-06-09 10:58:51 +0530
modified_at: 2022-06-09 12:38:26 +0530
---

## Problem Statement

- The next greater element of some element x in an array is the first greater element that is to the right of x in the same array.
- You are given two distinct 0-indexed integer arrays nums1 and nums2, where nums1 is a subset of nums2.
- For each 0 <= i < nums1.length, find the index j such that nums1[i] == nums2[j] and determine the next greater element of nums2[j] in nums2. If there is no next greater element, then the answer for this query is -1.
- Return an array ans of length nums1.length such that ans[i] is the next greater element as described above.


### Example

```

Input: nums1 = [4,1,2], nums2 = [1,3,4,2]
Output: [-1,3,-1]
Explanation: The next greater element for each value of nums1 is as follows:
- 4 is underlined in nums2 = [1,3,_4_,2]. There is no next greater element, so the answer is -1.
- 1 is underlined in nums2 = [_1_,3,4,2]. The next greater element is 3.
- 2 is underlined in nums2 = [1,3,4,_2_]. There is no next greater element, so the answer is -1.

```

## Meta Data

### Link 

- [Next Greater Element I - LeetCode](https://leetcode.com/problems/next-greater-element-i/)

### Tags 

- [[Stacks]]

### Similar 

- [[HR-next-greater-element]]

## Solution Approaches

### O( N^2 ) Naively Looping over for each element

- For each element in `nums1` find if there exists next in `nums2` by looping over

```python

ans=[]
for x in nums1:
	count=0
	i=nums2.index(x)+1
	while(i<len(nums2) and count==0):
		if nums2[i]>x:
			ans.append(nums2[i])
			count=1
		i+=1
	if count==0: ans.append(-1)
return ans

```


---

Return to [[DSA-Problems]]

---
