---
published : true

title : 
permalink : 
layout : note
excerpt : DSA Problem and Solution

alias : 
categories : problem
tags : 

questionLink : "https://practice.geeksforgeeks.org/problems/common-elements1132/1/#"
questionType : 

solvedDate : 2022-05-31 00:00:00 +0000
---

## Problem Statement

- Given three arrays sorted in increasing order. Find the elements that are common in all three arrays.

### Example

```

Input:
n1 = 6; A = {1, 5, 10, 20, 40, 80}
n2 = 5; B = {6, 7, 20, 80, 100}
n3 = 8; C = {3, 4, 15, 20, 30, 70, 80, 120}

Output: 20 80

Explanation: 20 and 80 are the only
common elements in A, B and C.

```

## Solution Approaches

### O( K ) Three pointer 

- K is length of the smallest array among A, B, C
- When All pointers point to the same value 
	- Check for duplicates
		- Add it to final answer
	- Increment the pointers
- Comparing current value with other array value
	- Increment pointer
- 

```cpp

vector <int> commonElements (int A[], int B[], int C[], int n1, int n2, int n3) {

	int i, j, k;
	i = j = k = 0;
	vector<int> ans;

	// loop until anyone passes beyond end
	while ((i < n1) && ((j < n2) && (k < n3))) {
		if ((A[i] == B[j]) && (B[j] == C[k])) {
			
			// add only if A[i] is not last element added to ans
			// or if its empty when it was empty
			if (ans.empty() or * ans.rbegin() != A[i]) {
				ans.push_back(A[i]);
			}

			i++;
			j++;
			k++;
		}
		else if (A[i] < B[j]) {
			i++;

		}
		else if (B[j] < C[k]) {
			j++;
		}
		else {
			k++;
		}
	}
	return ans;
}


```


---

Return to [[DSA-Problems]]

---
