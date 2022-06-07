---
published : true

title :  "Selection Sort"
permalink : "algo/sort/selection"
layout : note
excerpt : 

alias : "Selection Sort"
categories : ["algo","sort"]
tags : 

# date : 2022-05-29 00:00:00 +0000

showfooter : 
showgraph : 
created_at: 2022-06-04 15:23:51 +0530
modified_at: 2022-06-04 15:37:54 +0530
---

### Summary

- Complexity Analysis : `O(N^2) sO(1)`
- Not useful
	- Even in best case is `O(N^2)`
	- Might be useful when there is space constraint
- This is Not Stable Algorithm
	- Stable : If Duplicate elements order is preserved

```cpp

// DRY RUN
//////////

// 5 7 7 2 4 

// [5] <- current i
// <5  <- mininum to be swaped with
// (7) <- highlighted duplicate

//  | [5]  |   7   |   (7)   |   <2    |    4   |
//  |  2   |  [7]  |   (7)   |    5    |   <4   |
//  |  2   |   4   |  [(7)]  |   <5    |    7   |
//  |  2   |   4   |    5    | <[(7)]  |    7   |
//  |  2   |   4   |    5    |   (7)   |  <[7]  |
//  |  2   |   4   |    5    |   (7)   |    7   |

// inital : 5 7 (7)  2  4
// final  : 2 4  5  (7) 7
// order is not preserved

```

- Algorithm
	- Divide array into two parts, Left part is sorted and right isn't.
	- Iterate through the array and swap it minimum element in unsorted part
	- Stop when the iterator reaches the end.

```cpp

int getmndx(int arr[], int start, int end) {
	int mn = arr[start], mndx = start;
	for (int i = start; i < end; i++) {
		if (arr[i] < mn) {
			mn = arr[i]; mndx = i;
		}
	}
	return mndx;
}

void selection(int arr[], int n) {
	int i = 0;
	while (i < n) {
		int mndx = getmndx(arr, i, n);
		swap(arr[i], arr[mndx]);
		i++;
	}
}

int main() {
	int arr[] = { 7,5,4,2};
	int n = 4;
	selection(arr, n);

	for (int i = 0; i < n; i++) {
		cout << arr[i] << " ";
	}
}

// Dry Run
//////////


// |   i   |  mndx |    sorted  |  unsorted  |
// |   0   |   3   |    2       |   5 4 7    |
// |   1   |   1   |    2 4     |   5 7      |
// |   2   |   2   |    2 4 5   |   7        |
// |   3   |   3   |    2 4 5 7 |            |


```

---

Return to [[algo.sort|Sorting Algorithms]]

---
