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

solvedDate : 2022-05-16 00:00:00 +0000
---

## Problem Statement

- 

### Example

```
given 
return 


```

## Solution Approaches

### O(N) - [[cpp-stl-set]] 

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
