---
tags:
  - bfs
  - algorithm
---

![[Pasted image 20250315171059.png]]

---
```cpp
#include<iostream>
#include<algorithm>
#include<cstring>
#include<queue>

using namespace std;

const int N = 2e5+10;

int dx[] = {1,-1,10,-10,100,-100,300};                 
int dist[N];

struct Resource{
    int a,b,c,d;
}need;

void bfs(){
    //要遍历的东西是每个10-300的数字
    queue<int> q;
    q.push(10);
    q.push(300);
    //需要一个数组存每个数字所需要的步数
    //全部转换成-1
    memset(dist,-1,sizeof dist);

    dist[10] = 0;
    dist[300] = 1;
    //遍历每个节点
    while(!q.empty()){
        int x = q.front();
        q.pop();
        for(int i =0;i<7;i++){
            int nx = x + dx[i];
            //资源数目处于禁区就走,步数越来越多
            if(nx<10||nx>300) continue;
            if(dist[nx] != -1) continue;
            q.push(nx);
            //达到这个数的步数+1
            dist[nx] = dist[x]+1;
        }
    }
}
int main(){
    int T;cin>>T;
    bfs();
    while(T--){
        scanf("%d%d%d%d",&need.a,&need.b,&need.c,&need.d);
        printf("%d\n",dist[need.a]+dist[need.b]+dist[need.c]+dist[need.d]);
    }
    return 0;
}
```