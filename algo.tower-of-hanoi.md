---
published : true

title :  Tower of Hanoi
permalink : "/algo/toh"
layout : note
excerpt : 

alias : 
categories : "algo"
tags : 

# date : 2022-06-02 00:00:00 +0000

showfooter : 
showgraph : 
created_at: 2022-06-04 15:23:51 +0530
modified_at: 2022-06-04 15:23:51 +0530
---

### Printing Steps of TOH

```cpp

// start | box1 | source 
// end   | box3 | destination 
// other | box2 | helper 

void toh(int n, int start, int end) {
	

	if (n == 1) {
		cout << start << "->" << end << endl;
	}
	else {
		int other = 6 - (start + end);
		toh(n - 1, start, other);
		cout << start << "->" << end << endl;
		toh(n - 1, other, end);
	}
}

int main(){
	toh(3,1,2);
}

```


### Abort signal from abort(3) (SIGABRT)

```cpp

vector<int> ans;
void solve(int N, int &n, int box1, int box2, int box3) {
	if (N == 0 or n == 0) return;
	if (N == 1) {
		n--;
		if (n == 0) {
			ans.push_back(box1);
			ans.push_back(box3);
		}
		return;
	}
	solve(N - 1, n, box1, box2, box3);
	solve(1, n, box1, box3, box2);
	solve(N - 1, n, box2, box3, box1);
}


vector<int> shiftPile(int n, int k) {
	solve(n, k, 1, 3, 2);

}

int main() {
shiftPile(2,2);
}

```


--- 

Return to [[Algorithms|Algorithms]]

---
