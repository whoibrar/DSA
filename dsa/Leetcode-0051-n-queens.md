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

solvedDate : 2022-06-05 15:53:14 +0530


created_at: 2022-06-05 15:53:14 +0530
modified_at: 2022-06-05 16:08:22 +0530
---


#todo/retry -> `re(write) code for row wise traversal`
## Problem Statement

- 

### Example

```



```

## Solution Approaches

### Non-Optimized backtracking

#weirdbugincode

- This code doesn't work ?
	- gives no error and no output on local machine 
	- gives memory management error in leetcode 
	- I guess something with details but overall logic seems alright
- Solution from [L14. N-Queens - Leetcode Hard - Backtracking - YouTube](https://www.youtube.com/watch?v=i05Ju7AftcM)

```cpp

bool noAttacks(int row, int col, vector<string> board, int n) {
	// |     |     |     |
	// | --- | --- | --- |
	// | nw  | n   | ne  |
	// | w   | .   | e   |
	// | sw  | s   | se  |
	// | --- | --- | --- |
	// |     |     |     |

	// out of all 8 directions
	// [n ne e se s sw w nw]
	// as per recursion everythign on right is empty
	// so, dont check for anything moving towards right

	// now out of remaining checks to perform
	// we are adding only 1 queen per row
	// so we can essientially skip n and s as well

	// so only perform checks on
	// nw (upper diagonal)
	// w (horizontal)
	// sw (lower diagonal)


	int cpy_row = row;
	int cpy_col = col;

	// diagonal upper
	// move towards top left
	while (row >= 0 and col >= 0) {
		if (board[row][col] == 'Q') {return false;}
		row--; col--;
	}

	// lower diagonal
	// move towards bottom left
	row = cpy_row; col = cpy_col;
	while (row<n and col >= 0) {
		if (board[row][col] == 'Q') {return false;}
		row++; col--;
	}

	// towards lefet
	// move along the row towards left
	row = cpy_row; col = cpy_col;
	while (col >= 0) {
		if (board[row][col] == 'Q') {return false;}
		col--;
	}
	return true;

}

void solve(int col, vector<string> &board, vector<vector<string>> &ans, int n) {
	// for every col we are trying to add a queen

	// this condition is possible when we reach the end
	// hence adding the current board to answer and returning back

	if (col == n) {
		ans.push_back(board);
		return;
	}

	// before adding a queen at a location
	// check is she isn't being attacked
	// if not attacked then proceed further
	// to add a queen to next col

	for (int row = 0; row < n; row++) {
		if (noAttacks(row, col, board, n)) {
			board[row][col] = 'Q';
			solve(col + 1, board, ans, n);
			board[row][col] = '.';
		}
	}
}




vector<vector<string>> solveNQueens(int n) {
	vector<vector<string>> ans; // final answer to store all boards
	string s(n, '.'); // intializing the row of board
	vector<string>board(n, s); // the board

	vector<int> leftRow(n, 0), upperDia(2 * n - 1, 0), lowerDia(2 * n - 1, 0);
	solve(0, board, ans, n);


	for (int i = 0; i < n ; i++) {
		for (int j = 0; j < n; j++) {
			cout << ans[i][j];
		}
		cout << "---" << endl ;
	}
	return ans;
}

int main() {
	solveNQueens(3);

```


---

Return to [[DSA-Problems]]

---
