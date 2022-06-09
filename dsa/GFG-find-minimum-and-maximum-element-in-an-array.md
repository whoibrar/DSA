---
published : true

title : 
permalink : 
layout : note
excerpt : DSA Problem and Solution

alias : 
categories : problem
tags : 

questionLink : 
questionType : 

solvedDate : 2022-05-16 00:00:00 +0000
created_at: 2022-06-09 18:46:42 +0530
modified_at: 2022-06-09 18:46:42 +0530
---

## Problem Statement

- Given an array **A** of size **N** of integers. Your task is to find the **minimum and maximum** elements in the array.

### Example

```

Input:
N = 6
A[] = {3, 2, 1, 56, 10000, 167}
Output:
min = 1, max =  10000

```

## Solution Approaches

### O(N) - Intuitively Iteration and Comparison

- Initialize `max_val` and `min_val` to first element of array. 
- Iterate through array and compare with current value.
- Update whenever required.

```cpp

pair<long long, long long> getMinMax(long long a[], int n) {

    pair<long long, long long> ans (a[0],a[0]);

    for(int i=0;i<n;i++){
        if(a[i]<=ans.first) ans.first=a[i];
        if(a[i]>=ans.second) ans.second=a[i];
    }
    return ans;
}


```

using [[CPP STL Pair]] here!

---

Return to [[DSA-Problems]]

---
