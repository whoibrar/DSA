---
published : true

title : 
permalink : 
layout : note
excerpt : DSA Problem and Solution

alias : 
categories : problem
tags : 

questionLink : "https://leetcode.com/problems/sort-colors/"
questionCategories : "Arrays"

solvedDate : 2022-04-18 00:00:00 +0000
---

## Problem Statement

- Given an array consists of only `0,1,2`
- Sort in-place such that `0,0,...1,1,...2,2,...`


### Example

```
Input: nums = [2,0,2,1,1,0]
Output: [0,0,1,1,2,2]
```

## Solution Approaches

### Sorting | O(nlogn) | s O(1)

### Counting Sort | O(n+n) | s O(1)

```python
    def sortColors(self, nums: List[int]) -> None:
        count = [0,0,0]
        for i in nums:
            if i==0:
                count[0]+=1
            elif i==1:
                count[1]+=1
            else:
                count[2]+=1        

        i=0
        for x in range(count[0]):
            nums[i]=0
            i+=1
        for y in range(count[1]):
            nums[i]=1
            i+=1
        for z in range(count[2]):
            nums[i]=2
            i+=1
```

### O(N) sO(1) Counting Sorting

- Simply using [[algo.dutchNationalFlag|Dutch National Flag Algorithm]]


```cpp

// low = mid = 0
// high = len(a)-1


// assumptions
// [0 ... low-1] -> 0
// [high+1 ... END ] -> 2

// conditions check
// 0 { swap(a[low],a[mid]) low++ mid++ }
// 1 { mid++ }
// 2 { swap(a[mid],a[high]) high++ }

#include <bits/stdc++.h>
using namespace std;


void swapit(int &a, int &b) {
	int temp;
	temp = a;
	a = b;
	b = temp;
}
void sortColors(vector<int>& nums) {
	int low = 0;
	int mid = 0;
	int high = nums.size() - 1;
	while (mid <= high) {
		if (nums[mid] == 0) {
			swapit(nums[low], nums[mid]);
			low++; mid++;
		}
		else if (nums[mid] == 1) {
			mid++;
		}
		else if (nums[mid] == 2) {
			swapit(nums[mid], nums[high]);
			high--;
		}
	}
}


int main() {
	vector<int> arr = {2, 0, 2, 1, 1, 0};
	for (auto i : arr) {
		cout << i << " ";
	}
	sortColors(arr);
	cout << endl;
	for (auto i : arr) {
		cout << i << " ";
	}
}
```

---

Return to [[DSA-Problems|DSA Problems]]

---