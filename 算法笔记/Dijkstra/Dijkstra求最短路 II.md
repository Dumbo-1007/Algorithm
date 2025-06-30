---
tags:
  - dijkstra
  - 图
  - 最短路径
---
- 题目链接
	[850. Dijkstra求最短路 II](https://www.acwing.com/problem/content/852/)
- 题目
	![[Pasted image 20250427153616.png|500]]
- 思路
	
- 题解
```cpp
#include<iostream>
#include<algorithm>
#include<queue>
#include<vector>
#include<cstring>

using namespace std;
const int N = 150010;

struct edge{
  int v,w;
};

vector<edge> e[N];
int n,m;
int vis[N],dis[N];
//默认大顶对（less）大-->小
priority_queue<pair<int,int>> q;

void dijkstra(int s){
  memset(dis,0x3f,sizeof dis);
  dis[s] = 0;
  //利用大顶堆来排序，距离and下标
  q.push({0,s});
  while(q.size()){
    //not front();
    auto now = q.top();
    q.pop();
    int u = now.second;
    if(vis[u]) continue;
    vis[u] = 1;
    for(auto ed:e[u]){
      int v = ed.v;
      int w = ed.w;
      if(dis[v]>dis[u]+w){ 
        dis[v] = dis[u]+w;
        //忘了转换成大顶堆
        //用负值模拟小顶堆
        q.push({-dis[v],v});
      }
    }
  }
}

int main(){
  cin>>n>>m;
  for(int i = 1;i <= m;i++){
    int a,b,c;cin>>a>>b>>c;
    e[a].push_back({b,c});
  }
  dijkstra(1);
  cout<<(dis[n] == 0x3f3f3f3f ? -1:dis[n]);
  return 0;
}
```
