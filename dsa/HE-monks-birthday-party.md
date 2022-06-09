---
published : true

title : 
permalink : 
layout : note
excerpt : DSA Problem and Solution

alias : 
categories : problem
tags : 

created_at: 2022-06-09 17:25:48 +0530
modified_at: 2022-06-09 17:29:29 +0530
---

## Problem Statement

- Monk's birthday is coming this weekend! He wants to plan a Birthday party and is preparing an invite list with his friend Puchi. He asks Puchi to tell him names to add to the list.
- Puchi is a random guy and keeps coming up with names of people randomly to add to the invite list, even if the name is already on the list! Monk hates redundancy and hence, enlists the names only once.
- Find the final invite-list, that contain names without any repetition. 

### Example

```

Sample Input :

1 -> test cases
7 -> no of names
chandu
paro
rahul
mohi
paro
arindam
rahul

Sample Output :

arindam
chandu
mohi
paro
rahul



```

## Meta Data

### Link 

- [Monk's Birthday Party - Practice Problems](https://www.hackerearth.com/problem/algorithm/monks-birthday-party/)

### Tags 

- [[Sets]]

### Similar 

- 

## Solution Approaches

### O( N ) sO( N ) - Use a simple Set

- As sets are ordered in CPP, no need to sort again

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
