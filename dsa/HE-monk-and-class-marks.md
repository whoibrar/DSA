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

solvedDate : 2022-06-09 00:07:07 +0530


created_at: 2022-06-09 00:10:25 +0530
modified_at: 2022-06-09 00:37:11 +0530
---

## Problem Statement

- Monk is a multi-talented person, and prepares results for his college in his free time. (Yes, he is still in love with his old college!) He gets a list of students with their marks. The maximum marks which can be obtained in the exam is 100.

- The Monk is supposed to arrange the list in such a manner that the list is sorted in decreasing order of marks. And if two students have the same marks, they should be arranged in lexicographical manner.

- Help Monk prepare the same!

### Example

```

INPUT : 

3
Eve 78
Bob 99
Alice 78

OUTPUT : 

Bob 99
Alice 78
Eve 78

```

## Meta Data

### Link 

- [The Monk and Class Marks - Practice Problems](https://www.hackerearth.com/problem/algorithm/the-monk-and-class-marks/)

### Tags 

- [[CPP STL Set Multi]]

## Solution Approaches

### Using  MultiSet

- Create a map with marks and corresponding multiset to store the names of students
- Since we are already using a set don't need to sort anything

- Why use multiset and not set ?
	- Two students can have same name and marks
	- We need to consider this as well.

```cpp

int main() {
	map<int, multiset<string>> m;
	int n; cin >> n;
	while (n--) {
		string name; int marks; cin >> name >> marks;
		m[marks].insert(name);
	}

	// starts from end
	auto it = m.end(); it--;

	// runs till the first
	while (it != m.begin()) {
		auto mark = it->first;
		auto &students = it->second;

		for (auto name : students) {
			cout << mark << " " << name << endl;
		}
		it--;
	}

	// run once more for first
	auto mark = it->first;
	auto students = it->second;

	for (auto name : students) {
		cout << mark << " " << name << endl;
	}


}


```

The loop could be written better using a `while(true)` using the [[Dont Repeat Yourself]] Principle.

```cpp

auto it = m.end(); t--;

while(true){
	auto mark = it->first;
	auto &students = it->second;
	for (auto name : students) {
		cout << mark << " " << name << endl;
	}
	if(it==m.begin()){break;}	
	it--;
}


```

This can still be further improved using a few other tricks! We can instead store the negative value of the marks in the map itself and multiply by `-1` before output to balance it out. This way we can use the range based loop and make everything more clean.


```cpp

int main() {
	map<int, set<string>> m;
	int n; cin >> n;
	while (n--) {
		string name; int marks; cin >> name >> marks;
		m[-1 * marks].insert(name);
	}

	for ( auto &element : m) {
		auto marks = element.first;
		auto &students = element.second;

		for (auto student : students) {
			cout << student << " " << -1 * marks << endl;
		}
	}

}

```

There is even more clean and elegant way to sort elements by decreasing order by simply declaring at map.
- `map<int,string>>` becomes `map<int,string,greater<int>>`

```cpp
int main(){
	map< int, multiset<string>, greater<int> > m;
	int n; cin >> n;
	while (n--) {
		string name; int marks; cin >> name >> marks;
		m[marks].insert(name);
	}

	for ( auto &element : m) {
		auto marks = element.first;
		auto &students = element.second;

		for (auto student : students) {
			cout << student << " " << marks << endl;
		}
	}
}
```

---

Return to [[DSA-Problems]]

---
