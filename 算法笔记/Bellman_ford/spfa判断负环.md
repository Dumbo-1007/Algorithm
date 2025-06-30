---
tags:
  - spfa
  - 图
  - bellman-ford
---
- 原题链接
	[852. spfa判断负环](https://www.acwing.com/problem/content/854/)
- 题目
	![[Pasted image 20250503202552.png|600]]
- 思路
	
- 题解
```cpp
#include<iostream>
#include<algorithm>
#include<vector>
#include<cstring>
#include<queue>

using namespace std;
const int N = 1e5+10;

int n,m;
bool flag;
int vis[N],dis[N],cnt[N];
struct edge{
  int v,w;
};

vector<edge> e[N];
queue<int> q;

bool spfa(){
  //判整个图的负环要将每个节点都加入
  for(int i=1;i<=n;i++){     
    vis[i]=1;
    q.push(i);
  }
  
  while(q.size()){
    int now = q.front();
    q.pop();
    vis[now] = 0;
    for(auto ed:e[now]){
      int v = ed.v;
      int w = ed.w;
      if(dis[v] > dis[now] + w){
        dis[v] = dis[now] + w;
        cnt[v] = cnt[now] + 1;
        if(cnt[v]>=n) return true;
        if(!vis[v]) q.push(v),vis[v] = 1;
      }
    }
  }
  return false;
}
int main(){
  cin>>n>>m;
  for(int i = 1;i <= m;i++){
    int a,b,c;
    cin>>a>>b>>c;
    e[a].push_back({b,c});
  }
  flag = spfa();
  if(flag == false) cout<<"No";
  else cout<<"Yes";
  return 0; 
}
```