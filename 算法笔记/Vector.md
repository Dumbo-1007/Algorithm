---
tags:
  - vector
  - 数据结构
time: 2025-03-08T16:05:00
---
---
- **字符串的操作**
``` C++
#include <bits/stdc++.h>

using namespace std;
vector<int> a(10,-1);//10个-1
int main(){
  for(int i = 0;i<=a.size();i++) cout<<a[i]<<endl;
  for(auto x :a) cout<<x<<endl;
  for(auto& x :a) {//不加&的话，只会影响for中的x
	x = 1;
	cout<<x<<endl;
  }
  //常用的方法
  a.push_back(1);//尾插
  a.pop_back();
  a.pop_back(10);
  a.back();
  a.front();
  a.clear();
  a.empty();
  return 0;
}
```
---
```cpp
vector<int> a[N][N];
a[1][2].push_back(2);
a[1][2].push_back(4);
```
---
- **vector< pair<int,int> >**
	可变数组模式 ^5u3d4p
```cpp
#include<iostream>
#include<algorithm>
#include<cmath>
#include<vector>
#include<utility>
using namespace std;
const int N = 20;
vector< pair<int,int> > a;
int n;

int main(){
	cin>>n;
	for(int i = 1;i<=n;i++){
		// cin>>a[i].first;
		// cin>>a[i].second;
		int first,second;
		cin>>first>>second;
		a.push_back({first,second});
	}
	cout<<a[0].first;
	return  0;
}
```

---

```cpp
#include <iostream>
#include <algorithm>
#include <cmath>
#include <vector>
#include <utility>

using namespace std;
const int N = 20;

vector<pair<int, int>> a;
int n;

int main() {
	cin >> n;
	a.resize(n + 1); // 初始化 vector 大小为 n+1
	for (int i = 1; i <= n; i++) {
		cin >> a[i].first >> a[i].second;
	}
	cout << a[1].first << endl; // 输出 a[1].first
	return 0;
}
```
