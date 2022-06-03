---
published : true

title : 
permalink : 
layout : note
excerpt : DSA Problem and Solution

alias : 
categories : problem
tags : 

questionLink : "https://practice.geeksforgeeks.org/problems/cyclically-rotate-an-array-by-one2614/1#"
questionType : 

solvedDate : 2022-05-16 00:00:00 +0000
---

## Problem Statement

- Given an array, rotate the array by one position in clock-wise direction.

### Example

```

Input:
N = 5
A[] = {1, 2, 3, 4, 5}
Output:
5 1 2 3 4

```

## Solution Approaches

### O(N) - Swapping adjacent from right end

```cpp 

void rotate(int arr[], int n)
{
    for(int i=n-1;i>0;i--){
        swap(arr[i],arr[i-1]);
    }
}


```

---

Return to [[DSA-Problems]]

---
