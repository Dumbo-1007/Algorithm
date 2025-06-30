---
tags:
  - algorithm
time: 2025-02-15T13:29:00
---
- **模板**
``` Cpp
vector<int> a; // 记录每次排列 
vector<int> book; //标记是否被访问 

void DFS(int cur, int k, vector<int>& nums){
    if(cur == k){ //k个数已经选完，可以进行输出等相关操作 
        for(int i = 0; i < cur; i++){
			printf("%d ", a[i]);
		} 
        return ;
    }
    for(int i = 0; i < k; i++){ //遍历 n个数，并从中选择k个数 
        if(book[nums[i]] == 0){ //若没有被访问
            a.push_back(nums[i]); //选定本输，并加入数组 
            book[nums[i]] = 1; //标记已被访问 
            DFS(cur + 1, n, nums); //递归，cur+1 
            book[nums[i]] = 0; //释放，标记为没被访问，方便下次引用 
            a.pop_back(); //弹出刚刚标记为未访问的数
        }
    }
}
```
- **图的dfs模板**
```cpp
// 需要标记数组st[N],  遍历节点的每个相邻的便
void dfs(int u) {
   	st[u] = true; // 标记一下，记录为已经被搜索过了，下面进行搜索过程
   	for (int i = h[u]; i != -1; i = ne[i]) {
       	int j = e[i];
       	if (!st[j]) {
           	dfs(j);
       	}
   	}
}
```
---
- **指数型**
	适合需要在一串数中，找不同的组合：
	![[SmartSelect_20250331_102455_Samsung Notes.jpg|420]]
	- [[烤鸡]]
	- [[递归实现指数型枚举]]
	- [[PERKET]]
	- [[火柴棒等式]]
- **排列型**
	- [[全排列问题]]
	- [[n-皇后]]
- **组合型**
	- [[组合的输出]]
	- [[选数]]
	- [[数的划分]]
- **图与树**
	- [[树的重心]]
- **视频讲解**
	- [DFS正确入门方式 | DFS + 递归与递推习题课(下) | 一节课教你爆搜!](https://www.bilibili.com/video/BV1vy4y1Z7b2?spm_id_from=333.788.videopod.sections&vd_source=3d2791294cba8bd1dc5967d7f4d7dbcd)
	- [DFS正确入门方式 | DFS + 递归与递推习题课(上) | 一节课教你爆搜!](https://www.bilibili.com/video/BV1N24y1W7q4?spm_id_from=333.788.videopod.sections&vd_source=3d2791294cba8bd1dc5967d7f4d7dbcd)
---
- **习题**
	1. [[雫露露的背包]]
	2. [[自然数的拆分问题]]
	3. [[飞机降落]]