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

- Given an integer array nums, return all the triplets `[nums[i], nums[j], nums[k]]` such that `i != j`, `i != k`, and `j != k`, and `nums[i] + nums[j] + nums[k] == 0`.
- Notice that the solution set must not contain duplicate triplets.

### Example

```

Input: nums = [-1,0,1,2,-1,-4]
Output: [[-1,-1,2],[-1,0,1]]

```

## Solution Approaches

### O(N^2) sO(1) - Basically Three Pointers

- For every number `v[i]` check if we can find `v[r]` and `v[l]` such that `sum = v[i] + v[l] + v[r]==0` can be met.
- As its sorted we can use two pointer method for `v[r] and v[l]`

```cpp
vector<vector<int>> threesum(vector<int>& v) {
	vector<vector<int>> ans;
	int n = v.size();
	sort(v.begin(), v.end());

	for (int i = 0; i < n - 2; i++) {
		
		// skip the already computed ones aka repeat
		if (i > 0 and v[i] == v[i - 1]) {continue;}
		
		int l = i + 1, r = n - 1;
		
		while (l < r) {
			int sum = v[i] + v[l] + v[r];
			if (sum < 0) {l++;}
			else if (sum > 0) {r--;}
			else {
				
				// when condition is met
				vector<int> temp = {v[i], v[l], v[r]};
				ans.push_back(temp);
				
				// checking for repeating as sorted
				while (l < r and v[l] == v[l + 1]) {l++;}
				while (l < r and v[r] == v[r - 1]) {r--;}
				l++; r--;
			}
		}
	}
	return ans;
}

```

```python

def threeSum(self, nums: List[int]) -> List[List[int]]:

	n=len(nums)
	res=[]
	nums.sort()

	for i in range(n-2):

		if i>0 and nums[i]==nums[i-1]:
			continue

		l=i+1
		r=n-1

		while l<r:
			sum = nums[i]+nums[l]+nums[r]

			if sum<0:
				l=l+1

			elif sum>0:
				r=r-1

			else:
				res.append([nums[i],nums[l],nums[r]])
				while l<r and nums[l]==nums[l+1]: 
					l=l+1
				while l<r and nums[r]==nums[r-1]:
					r=r-1

				l=l+1
				r=r-1
	return res

```

---

Return to [[DSA-Problems]]

---
