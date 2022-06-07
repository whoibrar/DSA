---
published : true

title :  Linear Search Algorithm
permalink : "/algo/search/linear"
layout : note
excerpt : 

alias : ["Linear Search Algorithm"]
categories : "algo"
tags : 

# date : 2022-05-27 00:00:00 +0000

showfooter : 
showgraph : 
---

### O(N) - Classic Linear Search 
- Iterate through array, check for each index if current value is equal to k.
- If found return the index 
- If not found return -1 

```cpp

int search(int arr[], int n, int k) {
	// code here
	for(int i=0;i<=n;i++){
		if(arr[i]==k){
			return i;
		}
	}
	return -1;
}

```