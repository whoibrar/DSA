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
created_at: 2022-06-05 14:42:20 +0530
modified_at: 2022-06-05 15:28:23 +0530
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


### Accessing Elements in all 8 directions with single loop

Could've been useful for [[Leetcode-0051-n-queens]] if all you did was added queen to said location and recolor the locations it can access 

```cpp

8 -> Queen
1 -> Attack

|     |     |     |     |     |
| --- | --- | --- | --- | --- |
| .   | .   | 1   | .   | .   |
| 1   | .   | 1   | .   | 1   |
| .   | 1   | 1   | 1   | .   |
| 1   | 1   | 8   | 1   | 1   |
| .   | 1   | 1   | 1   | .   |
| 1   | .   | 1   | .   | 1   |


int addqueen(vector<vector<int>> &board, int i, int j) {
	int n = board.size();
	if (i >= n or j >= n) {return -1;}
	int idx = 0;

	while (idx < n) {
		
		// horizontal [i][0...n]	// vertial [0...n][j]
		if (idx < n) 
			{board[i][idx] = 1; board[idx][j] = 1;}
		
		// top left [0][0]
		if ((i - 1 - idx >= 0) and (j - 1 - idx >= 0)) 
			{board[i - 1 - idx][j - 1 - idx] = 1;}
		
		// bottom right [n][n]
		if ((i + 1 + idx < n) and (j + 1 + idx < n)) 
			{board[i + 1 + idx][j + 1 + idx] = 1;}
		
		// top right [0][n]
		if ( (i - 1 - idx >= 0) and (j + 1 + idx < n)) 
			{board[i - 1 - idx][j + 1 + idx] = 1;}
		
		// bottom left [n][0]
		if ( (i + 1 + idx < n) and (j - 1 - idx >= 0)) 
			{board[i + 1 + idx][j - 1 - idx] = 1;}
		idx++;
	}
	board[i][j] = 8;
	return 1;
}


```

|     |     |     |
| --- | --- | --- |
| nw  | n   | ne  |
| w   | .   | e   |
| sw  | s   | se  |
| --- | --- | --- |
|     |     |     |



---

Return to [[DSA-Problems]]

---
