---
tags:
  - Android
---

1. [【坑】导入项目报错Could not find com.android.tools.build:gradle:7.4.0-CSDN博客](https://blog.csdn.net/qq_56180303/article/details/129488968)
2. [解决default activity not found办法大全-CSDN博客](https://blog.csdn.net/baidu_27196493/article/details/100008417)
- 换源 
	`distributionUrl=https\://mirrors.cloud.tencent.com/gradle/gradle-8.10.2-bin.zip`
	<font color=#FF0211>！！</font>只换中间`mirrors.cloud.tencent.com/gradle/`的部分
	![[Pasted image 20250403134644.png|700]]
- 重装大法：
	- [android studio如何彻底卸载重装](https://blog.csdn.net/qq_46941656/article/details/119918496)
	- [安装环境SDK、Gradle配置](https://blog.csdn.net/keiraee/article/details/142321644)
- **镜像代码地址**：
```cpp
pluginManagement {
    repositories {
        maven { url=uri ("https://jitpack.io") }
        maven { url=uri ("https://maven.aliyun.com/repository/releases") }
//        maven { url 'https://maven.aliyun.com/repository/jcenter' }
        maven { url=uri ("https://maven.aliyun.com/repository/google") }
        maven { url=uri ("https://maven.aliyun.com/repository/central") }
        maven { url=uri ("https://maven.aliyun.com/repository/gradle-plugin") }
        maven { url=uri ("https://maven.aliyun.com/repository/public") }
        google()
        mavenCentral()
        gradlePluginPortal()
    }
}
dependencyResolutionManagement {
    repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)
    repositories {
        maven { url=uri ("https://jitpack.io") }
        maven { url=uri ("https://maven.aliyun.com/repository/releases") }
//        maven { url 'https://maven.aliyun.com/repository/jcenter' }
        maven { url=uri ("https://maven.aliyun.com/repository/google") }
        maven { url=uri ("https://maven.aliyun.com/repository/central") }
        maven { url=uri ("https://maven.aliyun.com/repository/gradle-plugin") }
        maven { url=uri ("https://maven.aliyun.com/repository/public") }
        google()
        mavenCentral()
    }
}
rootProject.name = "My Application"
include(":app")
```
---
- 同步我的仓库
1. [在Termux上使用git将项目提交到github_termux git-CSDN博客](https://blog.csdn.net/m0_74075298/article/details/127224691) 
2. [Termux：手机上的Linux神器 - 存储访问与文件传输教程-CSDN博客](https://blog.csdn.net/qq_53767308/article/details/126438281) 
3. [Termux将用户文件导入或导出操作【无root】_termius导出配置-CSDN博客](https://blog.csdn.net/qq_37435462/article/details/123303250?spm=1001.2101.3001.6650.2&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ECtr-2-123303250-blog-126438281.235%5Ev43%5Epc_blog_bottom_relevance_base4&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ECtr-2-123303250-blog-126438281.235%5Ev43%5Epc_blog_bottom_relevance_base4)  
---
- 加快网址的访问
1. 找到ping对应网站最快的站点：
	1. [多个地点Ping服务器,网站测速 - 站长工具](https://ping.chinaz.com/) 
	2. copy![[Pasted image 20250508173739.png|650]]
2. 找到文件夹`host`:  
	`C:\Windows\System32\drivers\etc`  
	![[Pasted image 20250508173651.png|400]]
3. 将最快的IP配置到hosts文件中
---
- [关于Button中设置背景\样式失效的问题及解决办法_androidbutton style背景颜色](https://blog.csdn.net/weixin_52089884/article/details/122616834)
- 

