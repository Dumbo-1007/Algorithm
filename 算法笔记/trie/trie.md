---
tags:
  - string
  - trie
  - 字符串统计
  - 数据结构
time: 2025-03-24T07:22:00
---
- 模板
	![[Pasted image 20250528111716.png|300]]
- **题目**
	![[Pasted image 20250324081618.png|600]]
---
- **视频**
	
---
- **思考**
	
---
- **题解**
```cpp
#include<iostream>
#include<algorithm>

using namespace std;

const int N = 1e5+10;
char str[N];
int son[N][26],cnt[N],idx;

void insert(char *str){
  int p = 0;
  for(int i =0;str[i];i++){
    //取出当前位，插入trie树中
    int u = str[i] - 'a';
    //如果没有该节点就创建
    if(!son[p][u]) son[p][u] = ++idx;
    p = son[p][u];  
  }
  cnt[p]++;
}

int query(char *str){
  int p = 0;
  for(int i = 0;str[i];i++){
    int u = str[i] - 'a';
    if(!son[p][u]) return 0;
    p = son[p][u];
  }
  return cnt[p];
}

int main(){
  int n;
  scanf("%d",&n);
  while(n--){
    char x[2];
    scanf("%s%s",x,str);
    if(*x == 'I') insert(str);
    else printf("%d\n",query(str));
  }
  return 0;
}
```
---
- **总结**
	
- **拓展**
	[[最大异或对]]
	