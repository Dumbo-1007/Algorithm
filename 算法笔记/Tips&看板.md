---
tags:
  - algorithm
  - 数据结构
---
- 结构体顺序问题 --> 不要声明顺序和写入顺序不一致
- cin>>n,m; --> cin>>n>>m;
- 插入代码块一定要用`ddd`,不然markdown用不了！！！
- 一串数组想要跳过自身来累加	
```cpp	
int st;
//找k个数相加
if(cnt==k) return ;
for(int i = st;i<=sizeof(a);i++){
	dfs(st+1,sum+a[i],cnt+1);
}
```


```tagcloud
```


 ---

