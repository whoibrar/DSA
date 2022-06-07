---
published : true

title :  "Bubble Sort"
permalink : "cs/algo/sort/bubble"
layout : note
excerpt : 

alias : "Bubble Sort"
categories : ["algo","sort"]
tags : 

# date : 2022-05-29 00:00:00 +0000

showfooter : 
showgraph : 
created_at: 2022-06-04 15:23:51 +0530
modified_at: 2022-06-04 15:36:17 +0530
---

### Summary 

- [[Etymology]] - Why it is Called so ?
	- Bubble sort gets its name from the fact that data "bubbles" to the top of the dataset.
	- Also "sinking sort" for the opposite reason, which is that some elements of data sink to the bottom of the dataset.

- How It works
	- In `i-th round`, `i-th largest element` is placed at right location.
	- After every `i-rounds`, `i-elements-from-end` are sorted.
	- It is Stable Algorithm

- Complexity Analysis
	- Time 
		- Best Case `O(N)` : Already Sorted
		- Worst Case `O(N^2)` : Reverse Sorted
	- Space :  `O(1)`

```cpp

void bubble(int arr[], int n) {
	int end = n - 1, start = 0;
	while (start <= end) {
		while (start + 1 <= end) {
			if (arr[start] > arr[start + 1]) {
				swap(arr[start], arr[start + 1]);
			}
			start++;
		}
		end--;
		start = 0;
	}
}

void bubble2(int arr[], int n) {
	bool noswaps = true;

	// this loop is for rounds
	for (int i = 0; i < n - 1; i++) {

		// swapping
		for (int j = 0; j < n - 1 - i; j++) {
			if (arr[j] > arr[j + 1]) {
				swap(arr[j], arr[j + 1]);
				noswaps = false;
			}
		}

		// this is possible only
		// if array is already sorted
		if (noswaps) {break;}
	}
}

int main() {
	int arr[] = { -7, -55, 4, 2};
	int n = 4;
	bubble(arr, n);

	for (int i = 0; i < n; i++) {
		cout << arr[i] << " ";
	}
}

```

---

Return to [[algo.sort|Sorting Algorithms]]

---