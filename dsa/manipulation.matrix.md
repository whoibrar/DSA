---
published : true

title : "Matrix Manipulation"
permalink : "dsa/matrix-manipulation"
layout : note
excerpt : 

alias : ["Matrix Manipulation"] 
categories : 
tags : 

# date : 2022-04-19 00:00:00 +0000

showfooter : 
showgraph : 
---

### Print Matrix

```cpp
for (int i = 0; i < matrix.size(); i++) {
	for (int j = 0; j < matrix[i].size(); j++) {
		cout << matrix[i][j] << " ";
	}
	cout << endl;
}
```

### Swapping Columns of Matrix

```cpp
// swapping the columns

int low = 0;
int high = matrix[0].size() - 1;

while (low < high) {
	for (int i = 0; i < matrix.size(); i++) {
		swap(matrix[i][low], matrix[i][high]);
	}
	low++; high--;
}
```

### Mirror Image of Square Matrix along diagonal

- This is same as Transpose of the matrix

```cpp
// turn into mirrored image along diagonal
	for (int i = 0; i < matrix.size(); i++) {
		for (int j = 0; j < i; j++) {
			swap(matrix[i][j], matrix[j][i]);
		}
	}
```

### Transpose of non-square Matrix 

- [[Leetcode-0867-transpose-matrix]]
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

```python

    def transpose(self, matrix: List[List[int]]) -> List[List[int]]:
        return [[matrix[i][j] for i in range(len(matrix))] for j in range(len(matrix[0]))]

```

---

Return to [[DSA-Problems]]

---
