---
tags:
  - dijkstra
  - 图
  - 最短路径
---
- 原题链接
	[849. Dijkstra求最短路 I](https://www.acwing.com/problem/content/851/)
- 题目
	![[Pasted image 20250427112150.png|500]]
- 题解
```cpp
#include<iostream>
#include<algorithm>
#include<vector>
#include<cstring>

using namespace std;
const int N = 5e2+10,M = 1e5+10;

struct edge{
  int v,w;
};

vector<edge> e[N];
int n,m;
int dis[N],vis[N];

void dijkstra(int s){
  memset(dis,0x3f,sizeof dis);
  dis[s] = 0;
  //遍历n-1次
  for(int i = 1;i<n;i++){
    //begin
    int u = 0;
    //从u点开始的每个点，找到距离最小的点并标记
    //深度体现在此
    for(int j = 1;j <= n;j++)
    //dis[u]>dis[j]写错了
      if(vis[j] == 0 && dis[u] > dis[j]) u=j;
    vis[u] = 1;
    //松弛操作
    for(auto ed:e[u]){
      int v = ed.v;
      int w = ed.w;
      if(dis[v] > dis[u]+w) dis[v] = dis[u]+w;
    }
  }
}

int main(){
  cin>>n>>m;
  for(int i = 1;i<=m;i++){
    int a,b,c;cin>>a>>b>>c;
    e[a].push_back({b,c});
  }
  dijkstra(1);
  cout<<(dis[n] == 0x3f3f3f3f ? -1 : dis[n]);
  return 0;
}
```
