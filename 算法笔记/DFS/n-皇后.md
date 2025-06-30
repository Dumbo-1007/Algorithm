---
tags:
  - dfs
  - 排列型
---
**原题链接**
- [n-皇后问题](https://www.acwing.com/problem/content/845/)
---
**题目**
![[Pasted image 20250422185846.png|600]]

---
- **思路**
	遍历每列，dfs每一行
---
- **题解**
```cpp
#include<iostream>
#include<algorithm>
#include<cstring>
using namespace std;
const int N = 19;
const int M = 20;
int a[N][N],n;
int x[N],y[N],cor[M],rcor[M];

void dfs(int cnt){
  if(cnt > n){
    for(int i = 1;i<=n;i++){
        for(int j = 1;j<=n;j++){
          if(a[i][j] == 0) cout<<'.';
          else cout<<"Q";
        }
        cout<<endl;
      }
    cout<<endl;
    return ;
  }
  // for(int i = 1;i<=n;i++){
  //   for(int j = 1;j<=n;j++){
  //     if(!x[i]&&!y[j]&&!cor[n+i - j]&&!rcor[i+j-1]&&!a[i][j]){
  //       x[i] = y[j] = cor[n+i-j] = rcor[i+j - 1] = 1;
  //       a[i][j] = 1; 
  //       dfs(cnt+1);
  //       a[i][j] = 0;
  //       x[i] = y[j] = cor[n+i-j] = rcor[i+j-1] = 0;
  //     } 
  //   }
  // }
    for(int j = 1;j<=n;j++){
      if(!x[cnt]&&!y[j]&&!cor[n+cnt-j]&&!rcor[cnt+j-1]&&!a[cnt][j]){
        x[cnt] = y[j] = cor[n+cnt-j] = rcor[cnt+j-1] = 1;
        a[cnt][j] = 1; 
        dfs(cnt+1);
        a[cnt][j] = 0;
        x[cnt] = y[j] = cor[n+cnt-j] = rcor[cnt+j-1] = 0;
      } 
    }
}
int main(){
  cin>>n;
  dfs(1);
  return 0;
}
```
---
- 误区：
![[Pasted image 20250509085202.png|700]]

