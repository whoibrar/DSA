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

- You are given two integer arrays `nums1` and `nums2`, sorted in **non-decreasing order**, and two integers `m` and `n`, representing the number of elements in `nums1` and `nums2` respectively.
- **Merge** `nums1` and `nums2` into a single array sorted in **non-decreasing order**.
- The final sorted array should not be returned by the function, but instead be _stored inside the array_ `nums1`. To accommodate this, `nums1` has a length of `m + n`, where the first `m` elements denote the elements that should be merged, and the last `n` elements are set to `0` and should be ignored. `nums2` has a length of `n`.


### Example

```

Input: nums1 = [1,2,3,0,0,0], m = 3, nums2 = [2,5,6], n = 3
Output: [1,2,2,3,5,6]

Explanation: The arrays we are merging are [1,2,3] and [2,5,6].
The result of the merge is [*1,*2,2,*3,5,6] with the *elements coming from nums1.

```

## Solution Approaches

### O(N) Backward Sorting

- Idea from [LeetCode Discuss](https://leetcode.com/problems/merge-sorted-array/discuss/600243/C%2B%2B-solution-O(m%2Bn)-solution-with-detailed-explanation.)
- Why Backwards and not forwards ?
	- There is free space (zeros) provided at the end of `nums1`
	- Starting from forwards will lead to collisions and overlapping
		- This overlapping might be resolved but will lead to a more complex and probably buggier code
	- So, if there was space provided at the beginning of `nums1` we would have started from there.


```cpp

void merge(vector<int>& nums1, int m, vector<int>& nums2, int n) {

	int i = m - 1; int j = n - 1; int k = m + n - 1;
	if (m == 0) {
		while (j >= 0) {
			nums1[j] = nums2[j];
			j--;
		}
		return;
	}

	while (i >= 0 && j >= 0) {
		if (nums1[i] > nums2[j]) {
			nums1[k--] = nums1[i--];
		}
		else {
			nums1[k--] = nums2[j--];
		}
		
		// one liner
		
	}
	while (j >= 0)
		nums1[k--] = nums2[j--];
}

```

---

Return to [[DSA-Problems]]

---
