---
tags:
  - spfa
  - 图
  - bellman-ford
---
- 原题链接
	[851. spfa求最短路](https://www.acwing.com/problem/content/853/)
- 题目
	![[Pasted image 20250503202431.png|600]]
- 思路
	
- 题解
```cpp
#include<iostream>
#include<algorithm>
#include<cstring>
#include<queue>
#include<vector>

using namespace std;
const int N = 1e5+10;
int n,m;
int dis[N],vis[N],cnt[N];
struct edge{
  int v,w;
};
vector<edge> e[2*N];

bool spfa(int s){
  memset(dis,0x3f,sizeof dis);
  dis[s] = 0;
  queue<int> q;
  q.push(s);
  vis[s] = 1;
  while(q.size()){
    auto u = q.front();
    q.pop();
    //标记入没入queue,只有入队之后才会有松弛
    vis[u] = 0;
    for(auto ed:e[u]){
      int v=ed.v;
      int w=ed.w;
      if(dis[v]>dis[u]+w){
        dis[v] = dis[u]+w;
        //一个点更新了这么多遍？？？
        cnt[v] = cnt[u] +1;
        if(cnt[v]>=n) return true;
        if(!vis[v]){
          q.push(v);
          vis[v] = 1; 
        } 
      }
    }
  }
  return false ;
}

int main(){
  cin>>n>>m;
  for(int i = 1;i<=m;i++){
    int a,b,c;
    cin>>a>>b>>c;
    e[a].push_back({b,c});
  }
  bool flag = spfa(1);
  if(dis[n] == 0x3f3f3f3f) puts("impossible");
  else cout<<dis[n];
  return 0;
}
```
