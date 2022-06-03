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

solvedDate : 2022-06-02 00:00:00 +0000
---

## Problem Statement

- Given a 2D integer array `matrix`, return _the **transpose** of_ `matrix`.
- The **transpose** of a matrix is the matrix flipped over its main diagonal, switching the matrix's row and column indices.

### Example

```

Input: matrix = [[1,2,3],[4,5,6],[7,8,9]]
Output: [[1,4,7],[2,5,8],[3,6,9]]


Input: matrix = [[1,2,3],[4,5,6]]
Output: [[1,4],[2,5],[3,6]]

```

## Solution Approaches

### O( M * N ) sO( N * M) Create and Add

- For a matrix of size `row * col` we need to create matrix of size `col * row` to store answer
- Now Transpose is basically swapping `mat[i][j]` with `mat[j][i]`
- So `ans[j][i]=mat[i][j]`


```cpp

vector<vector<int>> transpose(vector<vector<int>>& matrix) {
	int rows = matrix.size();
	int cols = matrix[0].size();

	vector<vector<int>> ans(cols, vector<int>(rows));
	for (int i = 0; i < matrix.size(); i++) {
		for (int j = 0; j < matrix[i].size(); j++) {
			ans[j][i] = matrix[i][j];
		}
	}

	return ans;
}


```

- Above Condensed into [[py.oneliners|Python OneLiner]]

```python

    def transpose(self, matrix: List[List[int]]) -> List[List[int]]:
        return [[matrix[i][j] for i in range(len(matrix))] for j in range(len(matrix[0]))]

```


---

Return to [[DSA-Problems]]

---
