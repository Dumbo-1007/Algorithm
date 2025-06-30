---
tags:
  - Huffman树
  - 贪心
---
- 原题链接： [148. 合并果子 - AcWing题库](https://www.acwing.com/problem/content/150/)
- 题目：
![[Pasted image 20250605112059.png|600]]
---
- 思路

---
- 题解
```cpp
#include<iostream>
#include<algorithm>
#include<cstring>
#include<queue>

using namespace std;

int main(){
  int n;cin>>n;
  priority_queue<int ,vector<int>,greater<int>> heap;
  while(n--){
    int a;cin>>a;
    heap.push(a);
  }
  int ans = 0;
  while(heap.size()>1){
    int a = heap.top();heap.pop();
    int b = heap.top();heap.pop();
    ans += (a+b);
    heap.push(a+b);
  }
  cout<<ans<<endl;
  return 0;
}
```