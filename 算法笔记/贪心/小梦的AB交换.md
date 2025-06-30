---
tags:
  - 贪心
  - 奇数
  - 交换
---
# 原题链接
- [小梦的AB交换](https://www.luogu.com.cn/problem/U535982)
## 题目描述

小梦有一个长度为 $2 * n$ 的 $AB$ 串 $s$，即 $s$ 中只包含 "$A$" 和 "$B$" 两种字符，且其中恰好有 $n$ 个 "$A$" 和 $n$ 个 "$B$"。
他可以对 $s$ 执行以下操作：
$\bullet$ 选择 $i, j\ (1 \leq i, j \leq 2\cdot n, i \ne j)$，并交换 $s_i$ 和 $s_j$。
他想知道，需要至少多少次操作，才能使得 $s$ 满足相邻的字符不相同，请你帮他算一算吧。
## 输入格式

**本题有多组测试数据。**

输入的第一行包含一个正整数 $T$，表示数据组数。

接下来包含 $T$ 组数据，每组数据的格式如下：

第一行一个正整数 $n$，表示 $s$ 长度的一半。

第二行一个长度为 $2*n$ 的字符串 $s$，保证只由 "$A$", "$B$" 两种字符构成。
## 输出格式

对于每组测试数据：

在单独的一行输出一个整数，表示最少进行的操作次数。

## 输入输出样例 #1

### 输入 #1
```
2
3
AAABBB
3
ABAABB
```

### 输出 #1
```
1
1
```
## 说明/提示

**【样例 1 解释】**

交换 $s_2 = A$ 和 $s_5=B$，得到 $s=$ "$\rm ABABAB$"，满足题意，一次交换即可。

**【数据范围】**

令 $N$ 表示 $T$ 组数据中 $n$ 的总和。

对于 $\rm 50\%$ 的数据有：$T = 1, 1 \leq N\leq 3$。

对于所有的测试数据有： $1 \leq T \leq 100, 1 \leq N \leq 10^6$。
## 题解
```cpp
#include<iostream>
#include<algorithm>

using namespace std;
const int N = 1e6+10;

char s[N];
int T;

int main(){
    cin>>T;
    while(T--){
        int cnt = 0;
        int n;cin>>n;
        for(int i = 1;i<=2*n;i++) cin>>s[i];
        for(int i = 1;i<=2*n;i++){
            if(i%2!=0){
                if(s[i]=='A') cnt++;
            }
        }
        cout<<min(cnt,n-cnt)<<endl;
    }
    return 0;
}
```
- [J-A 小梦的AB交换讲解](https://blog.csdn.net/zqystca/article/details/147028735)
