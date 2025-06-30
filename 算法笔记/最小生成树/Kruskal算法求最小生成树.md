---
tags:
  - kruskal
  - 图
---
- 题目链接
  [859. Kruskal算法求最小生成树](https://www.acwing.com/problem/content/861/)
- 题目
  ![[Pasted image 20250507083203.png|600]]
---
- 思路
  
---
- 题解
```cpp
#include<iostream>
#include<algorithm>
#include<vector>
#include<cstring>

using namespace std;
const int N = 2e5+10;

int n,m;
int f[N],vis[N];
int ans,cnt;
struct edge{
  int u,v,w;
  bool operator<(const edge&t)const {
    return w<t.w;
  }
}e[N];
//find root节点
int find(int x){
  if(f[x] == x) return x;
  return f[x] = find(f[x]);
}
bool kruskal(){
  //忘了sort
  sort(e,e+m);
  //每个点的根节点-->self
  for(int i = 0;i<=n;i++) f[i] = i;
  //遍历edge
  for(int i = 0;i<m;i++){
    //找root节点
    int x = find(e[i].u);
    int y = find(e[i].v);
    if(x!=y) {
      f[x] = y;
      ans += e[i].w;
      cnt++;
    }
  }
  return cnt == n-1;
}
int main(){
  cin>>n>>m;
  for(int i = 0;i<m;i++){
    int a,b,c;
    cin>>a>>b>>c;
    e[i].u = a;
    e[i].v = b;
    e[i].w = c;
  }
  bool flag = kruskal();
  if(flag == 0) puts("impossible");
  else cout<<ans;
  return 0;
}
```
