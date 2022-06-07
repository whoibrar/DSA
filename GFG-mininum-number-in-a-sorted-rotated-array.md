---
published : true

title : 
permalink : 
layout : note
excerpt : DSA Problem and Solution

alias : 
categories : problem
tags : 

questionLink : "https://practice.geeksforgeeks.org/problems/minimum-number-in-a-sorted-rotated-array-1587115620/1"
questionType : 

solvedDate : 2022-05-17 00:00:00 +0000
---

## Problem Statement

- Given an array of distinct elements which was initially sorted. 
- This array is rotated at some unknown point. 
- The task is to find the minimum element in the given sorted and rotated array.

### Example

```

Input:
N = 5
arr[] = {3,4,5,1,2}
Output: 1
Explanation: The array is rotated 
and the minimum element present is
at index (n-2) which is 1.

```

## Solution Approaches

### O(N) - Iterating from end 

```cpp

int minNumber(int arr[], int low, int high)
{
	if (arr[high] > arr[low]) {
		return arr[low];
	}
	else {
		while (arr[high - 1] < arr[high]) {
			high--;
		}
		return arr[high];
	}
}

```

### O(logN) - Binary Search 

- Implementing basic binary search using given `low, high and mid`. 
- The smallest value in `...5-1-2...` is the mid value. 
- This follows that pattern in sorted rotated array that `arr[mid-1] > arr[mid]` and also `arr[mid] < arr[mid+1]`.
- But this above condition will give error if the smallest value is found at ends of array or size of array is <3.
- To overcome this we can make use of sorted-array property.
	-  `arr[high]>arr[low]` is true when there is no rotation at all.
	- `arr[high-1]>arr[high]` is true when there is unit rotation.

```cpp

int minNumber(int arr[], int low, int high)
{
	if (arr[high] > arr[low]) {
		return arr[low];
	}
	else if (arr[high - 1] > arr[high]) {
		return arr[high];
	}
	else {
		int mid = (low + high) / 2;
		while (!(arr[mid - 1] > arr[mid] and arr[mid] < arr[mid + 1])) {
			mid = (low + high) / 2;
			if (arr[mid] > arr[high]) {low = mid;}
			else {high = mid;}
		}
		return arr[mid];
	}
}

```

---

Return to [[DSA-Problems]]

---
