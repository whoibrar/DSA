---
published : true

title : 
permalink : 
layout : note
excerpt : DSA Problem and Solution

alias : 
categories : problem
tags : 


created_at: 2022-06-09 18:47:36 +0530
modified_at: 2022-06-09 18:47:36 +0530
---

## Problem Statement

- Monk is standing at the door of his classroom. There are currently N students in the class, i'th student got Ai candies.
- There are still M more students to come. At every instant, a student enters the class and wishes to be seated with a student who has exactly the same number of candies. For each student, Monk shouts YES if such a student is found, NO otherwise.

### Example

```

Input:
First line contains an integer T. T test cases follow.
First line of each case contains two space-separated integers N and M.
Second line contains N + M space-separated integers, the candies of the students.

Output:
For each test case, output M new line, Monk's answer to the M students.
Print "YES" (without the quotes) or "NO" (without the quotes) pertaining to the Monk's answer.

Constraints:
1 ≤ T ≤ 10
1 ≤ N, M ≤ 105
0 ≤ Ai ≤ 1012

Sample Input :

1
2 3
3 2 9 11 2

Sample Output :

NO
NO
YES


```

## Meta Data

### Link 

- [Monk and his Friends - Hackerearth ](https://www.hackerearth.com/practice/data-structures/trees/binary-search-tree/practice-problems/algorithm/monk-and-his-friends/)

### Tags 

- [[Sets]] specifically [[CPP STL Set Unordered]]

### Similar 

- 

## Solution Approaches

### O( N ) sO( N ) Using a Set to store and Later Find

- Add given first `n` element directly to the set 
- For the rest perform the quires first and then add them to the set.

```cpp

#include <bits/stdc++.h>
using namespace std;


int main() {
	int t; cin >> t;
	while (t--) {
		int n, m; cin >> n >> m;
		unordered_set<long long int> s;

		// adding initial students
		for (int i = 0; i < n; i++) {
			long long temp; cin >> temp;
			s.insert(temp);
		}

		// m quries
		for (int i = 0; i < m; i++) {
			long long  temp; cin >> temp;
			if (s.find(temp) != s.end()) {
				cout << "YES" << endl;
			}
			else {
				cout << "NO" << endl;
			}
			s.insert(temp);
		}
	}



}

```


---

Return to [[DSA-Problems]]

---
