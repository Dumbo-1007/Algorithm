---
tags:
  - map
  - set
  - 数据结构
time: 2025-03-12T11:05:00
---
## 题目描述
给定 n 个盒子，你需要满足一下三种操作：
1. i j，把数字 i 扔到盒子 j 里面；
2. i，查询盒子 i 里面的数字，按升序输出；
3. i，查询数字 i 出现在的盒子编号，按升序输出。（**若多个同一数字出现在一个盒子，那么这个盒子编号只输出一次**。）
---
## 输入输出样例 #1
### 输入 #1
```
5
8
1 1 1
1 2 4
1 1 4
2 4
1 1 4
2 4
3 1
3 2
```
### 输出 #1
```
1 2
1 1 2
1 4
4
```
## 输入输出样例 #2
### 输入 #2
```
1
5
1 1 1
1 2 1
1 200000 1
2 1
3 200000
```
### 输出 #2
```
1 2 200000
1
```
---
### 题解
```cpp
#include<iostream>
#include<map>
#include<set>
using namespace std;

const int N  = 2e5+10;
map<int,set<int>> q;
multiset<int> mp[N];
int main(){
    int n;cin>>n;
    int t;
    cin>>t; 
    while(t--){
        int m;cin>>m;
        if(m == 1){
            int i;cin>>i;
            int j;cin>>j;
            mp[j].insert(i);
            q[i].insert(j);
        }
        if(m == 2){
            int i;cin>>i;
            for(auto a:mp[i]){
                cout<<a<<" ";
            }
            cout<<endl;
        }
        if(m == 3){
            int i;cin>>i;
            for(auto x:q[i]){
                cout<<x<<" ";
            }
            cout<<endl;
        }
    }
    return 0;
}
```
---
