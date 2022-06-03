---
published : true

title : 
permalink : 
layout : note
excerpt : DSA Problem and Solution

alias : 
categories : problem
tags : 

questionLink : "https://practice.geeksforgeeks.org/problems/move-all-negative-elements-to-end1813/1#"
questionType : 

solvedDate : 2022-05-16 00:00:00 +0000
---

## Problem Statement

- Given an unsorted array **arr[]** of size **N** having both negative and positive integers. The task is place all negative element at the end of array without changing the order of positive element and negative element.

### Example

```

Input : 
N = 8
arr[] = {1, -1, 3, 2, -7, -5, 11, 6 }

Output : 
1  3  2  11  6  -1  -7  -5

```

## Solution Approaches

### O(N) - Two pointer If order didn't matter 

- This approach could've been if relative order of elements didn't matter. 

```cpp 

void segregateElements(int arr[], int n)
{

	int low = 0, high = n - 1;
	while (low < high) {
		if ( arr[low] < 0 && arr[high] > 0) {swap(arr[low], arr[high]); low++; high--;}
		if ( arr[low] > 0 && arr[high] < 0) {low++; high--;}
		if ( arr[low] > 0 && arr[high] > 0) {low++;}
		if ( arr[low] < 0 && arr[high] < 0) {high--;}
	}
}

```

Also see [Move all negative numbers to beginning and positive to end with constant extra space - GeeksforGeeks](https://www.geeksforgeeks.org/move-negative-numbers-beginning-positive-end-constant-extra-space/)

### O(N) sO(N) - Positive from end and negative from other

- Using an additional array of size n
- Iterate through the given array and when positive element is encountered add it from left and if negative add from right.
- Iterate again to update the values

```cpp

void segregateElements(int arr[],int n){
	int val[n];
	int low = 0, high = n - 1;
	
	for (int i = 0; i < n; i++) {
		if (arr[i] < 0) {
			val[high--] = arr[i];
		}
		else {
			val[low++] = arr[i];
		}
	}
	
	int end = n - 1;
	for (int i = 0; i <= high; i++) {
		arr[i] = val[i];
	}
	for (int i = high + 1; i <= n - 1; i++) {
		arr[i] = val[end];
		end--;
	}
	
}

```

---

Return to [[DSA-Problems]]

---
