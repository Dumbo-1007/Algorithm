---
tags:
  - algorithm
time: 2025-02-15T13:29:00
---
- **模板**
``` Cpp
queue<node> q; 
void bfs(){ 
	while(!q.empty()) { 
		node temp=q.front(); 
		q.pop(); 
		if(完成目标) { 
			记录; 
			return; 
		} 
		for(int i=0;i<m;i++){//m为方向数组长度  
			int xx=temp.x+dx[i]; 
			int yy=temp.y+dy[i]; 
			if(下标越界||已被标记) continue;  
			mark[xx][yy]=1; 
			//注意，node{xx,yy}这种形式只适用于C++20及以上版本
			q.push(node{xx,yy});  
		} 
	}
} 
```
- **树与图**
```cpp

```
---
- **习题**
	1. [[孤岛]]
	2. [[D Tokitsukaze and Development Task]]
	3. [[P1443 马的遍历]]
	4. [[走迷宫]]
	5. [[八数码]]
	6. [[图中点的层次]]
	7. [[有向图的拓扑序列]]
	8. 

---
