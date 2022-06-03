---
published : true

title : 
permalink : 
layout : note
excerpt : DSA Problem and Solution

alias : 
categories : problem
tags : 

questionLink : "https://practice.geeksforgeeks.org/problems/finding-the-numbers0215/1#"
questionType : 

solvedDate : 2022-05-26 00:00:00 +0000
---

## Problem Statement

- Given an array A containing 2*N+2 positive numbers, out of which 2*N numbers exist in pairs whereas the other two number occur exactly once and are distinct. Find the other two numbers.

### Example

```

Input: 
N = 2
arr[] = {1, 2, 3, 2, 1, 4}

Output:
3 4

Explanation:
3 and 4 occur exactly once.

```

## Solution Approaches

### O(N) sO(1) - Bit Manipulation

- Mostly using [[Bit Manipulation]] xor property that `x^x=0`.
- Let required nos be x and y. we have`allxor` = `x^y`
- Now Least significant bit or the right most bit in `allxor` will be used to group the numbers in two different groups, this number is stored as `pos`
	- As having the LSB itself states that only one of x or y can have value of 1 at that position (`1^0=1`, `0^0=0`,`1^1=0`)
	- So the first group will be of elements of given array which have 1 in LSB, aka `pos`. 
	- Instead of storing them separately and later applying the xor, we can directly skip the array part and store the xor value itself `ans[0]`
- Now we have two separate groups (xor value) with only one number appearing once and rest in group appearing twice.
- But the property of xor (canceling out duplicates) we are left with the final required answers in `ans[0]` and `ans[1]`.

```cpp
vector<int> singleNumber(vector<int> v){
	int allxor = 0;
	for (int i = 0; i < v.size(); i++) {
		allxor = allxor ^ v[i];
	}


	int pos = allxor & (~(allxor - 1));
	vector<int> ans = {0,0};

	for (int i = 0; i < v.size(); i++)
	{
		if ((pos & v[i]) == pos) {ans[0] = (ans[0] ^ v[i]);}
		else {ans[1] = (ans[1] ^ v[i]);}
	}

	if(ans[0]>ans[1]){swap(ans[0],ans[1]);}
	return ans;
}

```

### Other Approaches 

- O(N) sO(N) - Using Maps and Basically Counting
- O(nLogN) sO(1) - Sorting and Checking Adjacent elements

---

Return to [[DSA-Problems]]

---
