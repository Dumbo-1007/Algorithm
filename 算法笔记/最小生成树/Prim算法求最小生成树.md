---
tags:
  - 图
  - prim
---
- 题目链接
  [858. Prim算法求最小生成树](https://www.acwing.com/problem/content/860/)
---
- 题目
  ![[Pasted image 20250507091034.png|600]]
---
- 思路  
  
---
- 题解
  1. 暴力法
```cpp
#include<iostream>
#include<algorithm>
#include<cstring>
#include<vector>

using namespace std;
const int N = 1e5+10;

struct edge{
  int v,w;
};
vector<edge> e[N];

int n,m;
int dis[N],vis[N],cnt,ans;

bool prim(int s){
  memset(dis,0x3f,sizeof dis);
  dis[s] = 0;
  for(int i = 1;i <= n;i++){
    //为什么u = 0?从头开始找离u最近的点
    int u = 0;
    for(int j = 1;j <= n;j++){
      if(!vis[j]&&dis[u]>dis[j]) u = j;
    }
    vis[u] = 1;
    //树外的点
    if(dis[u]!=0x3f3f3f3f) cnt ++;
    ans += dis[u];
    for(auto ed:e[u]){
      int v = ed.v,w = ed.w;
      if(dis[v] > w){
        dis[v] = w;
      }
    }
  }
  return cnt == n; 
}

int main(){
  cin>>n>>m;
  //无向图
  for(int i = 0;i<m;i++){
    int a,b,c;cin>>a>>b>>c;
    e[a].push_back({b,c});
    e[b].push_back({a,c});
  }
  bool flag = prim(1);
  if(!flag) puts("impossible");
  else cout<<ans;
  return 0;
}
```
  2. heap法
```cpp
#include<iostream>
#include<algorithm>
#include<cstring>
#include<vector>
#include<queue>

using namespace std;
const int N = 1e5+10;

struct edge{
  int v,w;
};
vector<edge> e[N];

int n,m;
int dis[N],vis[N],cnt,ans;

bool prim(int s){
  memset(dis,0x3f,sizeof dis);
  priority_queue<pair<int,int>> q;
  dis[s] = 0;
  q.push({dis[s],s});
  while(q.size()){
    auto u = q.top().second;
    q.pop();

    if(vis[u]) continue;
    vis[u] = 1;
    //不用判断dis-->limit,cnt++;
    cnt ++;
    ans += dis[u];
    for(auto ed:e[u]){
      int v = ed.v,w = ed.w;
      if(dis[v] > w){
        dis[v] = w;
        //换成大顶堆
        if(!vis[v]) q.push({-dis[v],v});
      }
    }
  }
  return cnt == n; 
}

int main(){
  cin>>n>>m;
  for(int i = 0;i<m;i++){
    int a,b,c;cin>>a>>b>>c;
    e[a].push_back({b,c});
    e[b].push_back({a,c});
  }
  bool flag = prim(1);
  if(!flag) puts("impossible");
  else cout<<ans;
  return 0;
}
```
---
