---
published : true

title : "Binary Search Algorithm"
permalink : "/algo/search/binary"
layout : note
excerpt : 

alias : ["Binary Search Algorithm"]
categories : "algo"
tags : 

# date : 2022-05-27 00:00:00 +0000

showfooter : 
showgraph : 
---

### O(LogN) - Classic Binary Search

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