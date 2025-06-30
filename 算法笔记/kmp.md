---
tags:
  - string
  - kmp
  - 数据结构
time: 2025-03-24T07:22:00
---
- **题目**
![[Pasted image 20250324071531.png|700]]
---
- **视频**
	[kmp](https://www.bilibili.com/video/BV18k4y1m7Ar/?spm_id_from=333.337.search-card.all.click)
---
- **思考**
	
---
- **题解**
```cpp
#include<iostream>
#include<algorithm>
using namespace std;
const int N = 100010,M = 1000010;
char p[N],S[M];
int ne[N];

int main(){
  int n;cin>>n;
  scanf("%s",p+1);
  int m;cin>>m;
  scanf("%s",S+1);
  //设置next数组
  for(int i = 2,j = 0;i<=n;i++){
    while(j&&p[i]!=p[j+1]) j = ne[j];
    if(p[i] == p[j+1]) j++;
    ne[i] = j;
  }
  //KMP
  for(int i = 1,j = 0;i<=m;i++){
    while(j&&S[i]!=p[j+1]) j = ne[j];
    //对比成功
    if(S[i] == p[j+1]) j++;
    //匹配到了
    if(j == n){
      printf("%d ",i-j);
      j = ne[j];
    }
  }
  return 0;
}
```
---
- **总结**
	