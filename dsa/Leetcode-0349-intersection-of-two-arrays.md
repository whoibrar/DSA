---
published : true

title : 
permalink : 
layout : note
excerpt : DSA Problem and Solution

alias : 
categories : problem
tags : 

created_at: 2022-06-09 18:46:53 +0530
modified_at: 2022-06-09 19:02:40 +0530
---

## Problem Statement

- Given two integer arrays nums1 and nums2, return an array of their intersection. Each element in the result must be unique and you may return the result in any order.

### Example

```

Input: nums1 = [1,2,2,1], nums2 = [2,2]
Output: [2]

```

## Solution Approaches

### O(N) - [[CPP STL Set]] 

```cpp

vector<int> intersection(vector<int>& nums1, vector<int>& nums2) {
	set<int> s1, s2;
	for(int i=0;i<nums1.size();i++){
		s1.insert(nums1[i]);
	}
	for(int i=0;i<nums2.size();i++){
		s2.insert(nums2[i]);
	}
	set<int> unique;
	set_intersection(s1.begin(),s1.end(),s2.begin(),s2.end(),inserter(unique,unique.begin()));
	
	vector<int> v;
	for(auto i : unique){
		v.push_back(i);
	}
	return v;
}

```

###  [[py.oneliners]]  - List Comprehension

```python 

def intersection(self, nums1: List[int], nums2: List[int]) -> List[int]:
	return set([x for x in nums2 if x in nums1])

```

---

Return to [[DSA-Problems]]

---
