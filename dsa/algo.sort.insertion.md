---
published : true

title :  "Insertion Sort"
permalink : "/algo/sort/insertion"
layout : note
excerpt : 

alias : "Insertion Sort"
categories : ["algo","sort"]
tags : 

# date : 2022-05-29 00:00:00 +0000

showfooter : 
showgraph : 
created_at: 2022-06-04 15:23:51 +0530
modified_at: 2022-06-04 15:36:30 +0530
---

### Summary 

- Iterate through the loop, elements before it are in sorted position so place the current iterator in position(sorted among current iterated, left side)

- Complexity Analysis
	- Time 
		- Best Case : `O(N)`
		- Worst Case : `O(N^2)`
	- Space : `O(1)`


```cpp

void insertion(int arr[], int n) {
	for (int i = 1; i < n; i++) {
		int temp = arr[i];
		int j = i - 1;
		for (; j >= 0; j--) {
			if (arr[j] > temp) {
				arr[j + 1] = arr[j];
			}
			else {
				break;
			}
		}
		arr[j + 1] = temp;
	}
}

```

---

Return to [[algo.sort|Sorting Algorithms]]

---
