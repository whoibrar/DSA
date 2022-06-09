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

solvedDate : 2022-06-09 17:18:25 +0530


created_at: 2022-06-09 17:22:16 +0530
modified_at: 2022-06-09 19:07:31 +0530
---

## Problem Statement

- Sherlock is investigating that who was responsible for the massacre at the British embassy in Tbilisi.
- AMMO codeword signifies something. What can be its meaning?
- Sherlock is suspecting some people , and each of them has some jealousy coefficient.
- Consider yourself to be Dr.Watson. You need to arrange these names in decreasing order of jealousy.
- If two or more people have same jealousy coefficient , they must be arranged in lexicographical order. 

### Example

```

Input :
	On the first line, you are provided the value N - the number of people Sherlock suspects.
	N lines follow.
	Each of these N lines comprises a string S and an integer X, signifying the name and the associated jealousy coefficient respectively.

Output :
	Print the N lines in the order specified above.

Constraints :
	1<=N<=100000
	1<=X<=1000
	1<=|S|<=100

Sample Input
	3
	Smallwood 3
	Vivian 5
	Norbury 5

Sample Output :
	Norbury 5
	Vivian 5
	Smallwood 3

```

## Meta Data

### Link 

- [Sherlock and his AMMO quest - Practice Problems](https://www.hackerearth.com/problem/algorithm/stl/)

### Tags 

- [[CPP STL Map]] and [[CPP STL Set]]

### Similar 

- [[HE-monk-and-class-marks]]

## Solution Approaches

### O( N ) Adding to Map of Set of Strings

- Same approach from [[HE-monk-and-class-marks]], see that for more info!

```cpp

#include <bits/stdc++.h>
using namespace std;


int main() {
	int n; cin >> n;
	map<int, multiset<string>> m;
	while (n--) {
		string name; int val;
		cin >> name >> val;
		m[-1 * val].insert(name);
	}
	for (auto i : m) {
		auto val = i.first;
		auto names = i.second;
		for (auto name : names) {
			cout << name << " " << -1 * val << endl;
		}
	}

}

```


---

Return to [[DSA-Problems]]

---
