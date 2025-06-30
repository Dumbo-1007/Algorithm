---
tags:
  - 排序
  - sort
  - algorithm
time: 2025-02-15T13:29:00
---
- **_用法_**
	1. 它有三个参数`sort(begin, end, cmp)`
		- begin为指向待sort()的数组的第一个元素的指针
		- end为指向待sort()的数组的最后一个元素的下一个位置的指针 
		- cmp参数为排序准则，cmp参数可以不写，如果不写的话，默认从小到大进行排序
	2. 大到小排序：将cmp参数写为`greater<int>()`就是对int数组进行排序，当然`<xxx>`中我们也可以写double、long、float等
	3. 其他的排序准则，那么就需要我们自己定义一个bool类型的函数来传
---
- **实例**
``` Cpp
#include<iostream>
#include<algorithm>
#include<vector>

using namespace std;

vector<int> a = {2,3,1,4,8,5,6,0};
struct pai{
	int first,second;
};
bool cmp(int x,int y){
	return x % 10 > y % 10;
}

int main(){
	vector<pai> c;
	c.push_back({2,4});
	c.push_back({1,2});
	c.push_back({3,1});
	sort(c.begin(),c.end(),[](pai a,pai b){
		return a.first>b.first;
	});
	for(auto [first,second]:c){
	  cout<<first<<" "<<second<<endl;
	}
	
	int n = 10;
	int num[n] = {65,59,96,13,21,80,72,33,44,99};
	sort(num,num+n,cmp);
	sort(a.begin(),a.end(),greater<>());
	for(int i=0;i<10;i++){
		cout<<num[i]<<" ";
	}
	cout<<endl;
	
	vector<pair<int,int>> d;
	d.push_back({4,4});
	d.push_back({7,2});
	d.push_back({2,3});
	sort(d.begin(),d.end());
	for(auto e:d){
		cout<<e.first<<" "<<e.second<<endl;
	}
	return 0;
	/*3 1
    2 4
    1 2
    59 99 96 65 44 13 33 72 21 80 
    2 3
    4 4
    7 2*/
} 
```
---
- 详解 
	[C++ sort()排序详解-CSDN博客](https://blog.csdn.net/qq_41575507/article/details/105936466)
---


