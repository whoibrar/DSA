---
published : true

title : 
permalink : 
layout : note
excerpt : DSA Problem and Solution

alias : 
categories : problem
tags : 

questionLink : "https://practice.geeksforgeeks.org/problems/find-the-frequency/1#"
questionType : 

solvedDate : 2022-05-17 00:00:00 +0000
---

## Problem Statement

- Given a vector of **N** positive integers and an integer **X**. The task is to find the **frequency** of X in vector.

### Example

```

Input:
N = 5
vector = {1, 1, 1, 1, 1}
X = 1
Output: 
5
Explanation: Frequency of 1 is 5.

```

## Solution Approaches

### O(N) - Naively Iteration and counting 

```cpp

int findFrequency(vector<int> v, int x){
    // Your code here
    int count = 0;
    for(int i=0;i<v.size();i++){
        if (v[i]==x) count++;
    }
    return count;
}

```

---

Return to [[DSA-Problems]]

---
