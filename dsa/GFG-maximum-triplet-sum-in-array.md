---
published : true

title : 
permalink : 
layout : note
excerpt : DSA Problem and Solution

alias : 
categories : problem
tags : 

questionLink : "https://practice.geeksforgeeks.org/problems/maximum-triplet-sum-in-array0129/1/#"
questionType : 

solvedDate : 2022-06-06 22:14:15 +0530


created_at: 2022-06-06 22:14:15 +0530
modified_at: 2022-06-06 22:42:50 +0530
---

## Link 

- [Maximum triplet sum in array - GeeksforGeeks](https://www.geeksforgeeks.org/maximum-triplet-sum-array/)

## Problem Statement

- Given an array, the task is to find the maximum triplet sum in the array.

### Example

```

Input : arr[ ] = {1, 0, 8, 6, 4, 2} 
Output : 18 

```

## Solution Approaches

### O(N) Three Pointer Traversal 

- The three pointers `first, second, thrid` are initialized to the respective largest elements amongst the first three of the array
- Traverse through the array and update the pointers 
	- This can be done by swapping one for the other

```cpp

int maxTripletSum(int arr[], int n) {

	int first, second, third;
	// storing the indexes 

	first = max(arr[0], max(arr[1], arr[2]));
	third = min(arr[0], min(arr[1], arr[2]));

	for (int i = 0 ; i < 3 ; i++) {
		if (arr[i] == first) {first = i; break;}
	}
	for (int i = 0 ; i < 3 ; i++) {
		if (arr[i] == third) {third = i; break;}
	}
	second = 3 - (first + third);
	for (int i = 3; i < n; i++) {
		if (arr[i] > arr[first]) {
			third = second; second = first; first = i;
		}
		else if (arr[i] > arr[second]) {
			third = second; second = i;
		}
		else if (arr[i] > arr[third]) {
			third = i;
		}
	}
	return arr[first] + arr[second] + arr[third];
}

```

### O(N) Basically Above but slightly optimized

- The above code runs O(3)+O(N) times which can be further optimized using the below technique 
- Instead of storing the indexes we are now storing the actual `first, second, thrid` largest elements in the variables and iterating through the loop
- now we can skip the initial part and have the loop run only one time

```cpp

	int first = INT_MIN, second = INT_MIN, third = INT_MIN;
	// storing the values

	for (int i = 0; i < n; i++) {
		if (arr[i] > first) {
			third = second; second = first; first = arr[i];
		}
		else if (arr[i] > second) {
			third = second; second = arr[i];
		}
		else if (arr[i] > third) {
			third = arr[i];
		}
	}
	return first + second + third;

```


---

Return to [[DSA-Problems]]

---
