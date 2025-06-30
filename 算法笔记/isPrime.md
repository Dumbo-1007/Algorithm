---
tags:
  - 判断素数
  - algorithm
---
由于n的因数总是成对出现的，且分别分布在$[$ $1$,  $\sqrt{n}$ $]$和$[$ $\sqrt{n}$, $n$ $]$范围内（若因数为$\sqrt{n}$，我们当作两个重复的因数），那么我们只需判断一个范围即可。代码如下：
```cpp
bool isPrime(int n){
	bool yes = true;
	for(int i = 2;i<=sqrt(n);i++){
		if(n%i == 0){
			yes = false;
			break;
		}
	}
	return yes;
}
```
---
