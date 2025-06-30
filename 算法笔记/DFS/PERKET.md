---
tags:
  - dfs
  - 指数型
  - pair
---
# 原题link
- [P2036 [COCI 2008/2009 #2] PERKET ](https://www.luogu.com.cn/problem/P2036)
## 题目描述
Perket 是一种流行的美食。为了做好 Perket，厨师必须谨慎选择食材，以在保持传统风味的同时尽可能获得最全面的味道。你有 $n$ 种可支配的配料。对于每一种配料，我们知道它们各自的酸度 $s$ 和苦度 $b$。当我们添加配料时，总的酸度为每一种配料的酸度总乘积；总的苦度为每一种配料的苦度的总和。
众所周知，美食应该做到口感适中，所以我们希望选取配料，以使得酸度和苦度的绝对差最小。
另外，我们必须添加至少一种配料，因为没有任何食物以水为配料的。
## 输入格式
第一行一个整数 $n$，表示可供选用的食材种类数。
接下来 $n$ 行，每行 $2$ 个整数 $s_i$ 和 $b_i$，表示第 $i$ 种食材的酸度和苦度。
## 输出格式
一行一个整数，表示可能的总酸度和总苦度的最小绝对差。
## 输入输出样例 #1
### 输入 #1
```
1
3 10
```
### 输出 #1
```
7
```
## 输入输出样例 #2
### 输入 #2
```
2
3 8
5 8
```
### 输出 #2
```
1
```
## 输入输出样例 #3
### 输入 #3
```
4
1 7
2 6
3 8
4 9
```
### 输出 #3
```
1
```
## 说明/提示
对于 $100\%$ 的数据，有 $1 \leq n \leq 10$，且将所有可用食材全部使用产生的总酸度和总苦度小于 $1 \times 10^9$，酸度和苦度不同时为 $1$ 和 $0$。

---
## 题解
```cpp
#include <iostream>
#include <algorithm>
#include <cmath>
#include <vector>
#include <utility>

using namespace std;
const int N = 20;

vector<pair<int, int>> a;
int n;
int res = 1e9;
vector<int> q[N];
void dfs(int cnt){
    if(cnt>n){
        int suan = 1;
        int ku = 0;
        for(int i = 1;i<=n;i++){
        	if(!q[i].empty()&&q[i][0] == 1){
        		suan=suan*a[i].first;
            	ku+=a[i].second;
            	res = min(res,abs(suan - ku));
        	}
    	}
    	return ;
    } 
    
    for(int i = 0 ;i<=1;i++){
        q[cnt].push_back(i);
        dfs(cnt+1);
        q[cnt].pop_back();
    }
}

int main() {
    cin >> n;
    a.resize(n + 1); // 初始化 vector 大小为 n+1
    for (int i = 1; i <= n; i++) {
        cin >> a[i].first >> a[i].second;
    }
    dfs(1);
    cout<<res;
    return 0;
}
```
---
[[Vector#^5u3d4p]]

