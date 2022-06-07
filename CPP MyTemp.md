---
published : true

title : "CPP MyTemp"
permalink : "/cpp/temp"
layout : note
excerpt : 

alias : 
categories : "cpp"
tags : 

# date : 2022-06-05 00:00:00 +0000

showfooter : 
showgraph : 

created_at: 2022-06-05 16:07:58 +0530
modified_at: 2022-06-05 16:07:58 +0530
---

#todo/code ->
```
- Use templates to replace multiple function calls
- Check other peoples templates on YT / Codeforces
- Use what works
```


```cpp

#include <bits/stdc++.h>
using namespace std;

void getar(int a[], int n);
void getar(string a[], int n);
void setar(int a[], int n);
void getv(vector<int> v);
void getv(vector<string> v);
void getvv(vector<vector<int>> v);








int main() {

// INPUT
////////

	// int n; cin >> n; int arr[n]; setar(arr, n); getar(arr, n);
	// int n; cin >> n; int arr1[n]; setar(arr1, n); // getar(arr1, n);
	// int m; cin >> m; int arr2[m]; setar(arr2, m); // getar(arr2, m);
	// vector<int> v {1,3,5,6}; int n = 4;

// FUNC
///////

}


















void getv(vector<string> v) {
	int n = v.size();
	cout << "---" << "[";
	for (int i = 0; i < n - 1; i++) {
		cout << v[i] << ", ";
	}
	cout << v[n - 1] << "]" << "---";
}

void getv(vector<int> v) {
	int n = v.size();
	cout << "---" << "[";
	for (int i = 0; i < n - 1; i++) {
		cout << v[i] << ", ";
	}
	cout << v[n - 1] << "]" << "---";
}

void getar(int a[], int n) {
	cout << "---" << "[";
	for (int i = 0; i < n - 1; i++) {
		cout << a[i] << ", ";
	}
	cout << a[n - 1] << "]" << "---";
}

void getar(string a[], int n) {
	cout << "---" << "[";
	for (int i = 0; i < n - 1; i++) {
		cout << a[i] << ", ";
	}
	cout << a[n - 1] << "]" << "---";
}

void setar(int a[], int n) {
	for (int i = 0; i < n; i++) {
		cin >> a[i] ;
	}
}

void getvv(vector<vector<int>> v) {
	for ( auto row : v) {
		getv(row);
		cout << endl;
	}
}

```