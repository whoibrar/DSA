---
published : true

title : 
permalink : 
layout : note
excerpt : DSA Problem and Solution

alias : 
categories : problem
tags : 

questionLink : "https://practice.geeksforgeeks.org/problems/merge-two-sorted-arrays5135/1#"
questionType : 

solvedDate : 2022-06-01 00:00:00 +0000
---

## Problem Statement

- Given two sorted arrays arr1[] of size N and arr2[] of size M. Each array is sorted in non-decreasing order. Merge the two arrays into one sorted array in non-decreasing order without using any extra space.

### Example

```

Input:
N = 4, M = 5
arr1[] = {1, 3, 5, 7}
arr2[] = {0, 2, 6, 8, 9}

Output: 0 1 2 3 5 6 7 8 9

Explanation: Since you can't use any 
extra space, modify the given arrays
to form 
arr1[] = {0, 1, 2, 3}
arr2[] = {5, 6, 7, 8, 9}

```

## Solution Approaches

### O( N * LogN ) Comparing from ends 

- Iterate the first array from end to start and Second array from start to end
- Swap if second is lesser than the first one's

```cpp

void merge2(int nums1[], int n, int nums2[], int m) {

	int i = n - 1; int j = 0;

	while (i >= 0 && j < m) {
		if (nums1[i] > nums2[j]) {
			swap(nums1[i], nums2[j]);
			i--;
		}
		j++;
	}

	sort(nums1, nums1 + n);
	sort(nums2, nums2 + m);

}

```



---

Return to [[DSA-Problems]]

---
