---
published : true

title : 
permalink : 
layout : note
excerpt : DSA Problem and Solution

alias : 
categories : problem
tags : 

questionLink : "https://practice.geeksforgeeks.org/problems/reverse-an-array/0#"
questionType : 

solvedDate : 2022-05-16 00:00:00 +0000
---

## Problem Statement

- Given an array, reverse it, For given test cases.

### Example

```

Input:
1
4
1 2 3 4

Output:
4 3 2 1

```

## Solution Approaches

### O(N) - Intuitively  Swapping elements from first and last

```cpp

int t;
cin >> t;
while(t--){
	int n;
	cin >> n;
	
	int a[n];
	for(int i=0;i<n;i++){
		cin >> a[i];
	}
	
	int low=0,high=n-1;
	while(low<high){
		swap(a[low],a[high]);
		low++; high--;
	}
	
	for(auto x : a){
		cout << x << " ";
	}
	cout << endl;
}

```

---

Return to [[DSA-Problems]]

---
