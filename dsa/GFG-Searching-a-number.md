---
published : true

title : 
permalink : 
layout : note
excerpt : DSA Problem and Solution

alias : 
categories : problem
tags : 

questionLink : "https://practice.geeksforgeeks.org/problems/searching-a-number0324/1/#"
questionType : 

solvedDate : 2022-05-16 00:00:00 +0000
---

## Problem Statement

- Given an array **Arr** of **N** elements and a integer **K**. Your task is to return the position of **first occurence** of **K** in the given array.
- Array index starts with 1.

### Example

```
Input:
N = 5, K = 16
Arr[] = {9, 7, 2, 16, 4}

Output: 4

Explanation: K = 16 is found in the
given array at position 4.
```

## Solution Approaches

### O(N) - Classic Linear Search 
- Implementation of [[algo.search.linear|Linear Search Algorithm]] 
- Iterate through array, check for each index if current value is equal to k.
- If found return the index+1 as indexing starts with 1
- If not found return -1 as asked.

```cpp

int search(int arr[], int n, int k) {
	// code here
	for(int i=0;i<=n;i++){
		if(arr[i]==k){
			return i+1;
		}
	}
	return -1;
}

```

### O(LogN) - Classic Binary Search

- Implementation of [[algo.search.binary|Binary Search Algorithm]]

```cpp

int findnum(int arr[], int low, int high, int x) {
	if (high >= low) {
		int mid = (low + high) / 2;
		if (arr[mid] == x) {
			return mid;
		}
		else if (arr[mid] > x) {
			return findnum(arr, low, mid - 1, x);
		}
		else if (arr[mid] < x) {
			return findnum(arr, mid + 1, high, x);
		}
	}
	return -1;
}


```

---

Return to [[DSA-Problems]]

---
