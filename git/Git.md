---
tags:
  - git
---
![[1 Git、GitHub 和 Gitee 完整讲解：从基础到进阶功能.pdf]]

---
- **在github/gitee创建仓库**
	![[Pasted image 20250326071119.png]]
- **初始化本地仓库**
	![[Pasted image 20250326071208.png]]
	- 想其他命令行程序，甚至是 cmd 都可以，只需使用 cd 命令进入这个项目目录即可
- **配置自己的信息**
	- `git config user.name "your name" --global`
	- `git config user.email "your email" --global`
- **初始化仓库**
	`git init`
- **添加远程仓库**
	- 添加远程仓库的位置，让本地仓库能够知道这个仓库应该推送到哪里
	- 打开我们之前在 Github 上创建的仓库，单击 SSH按钮，然后点击 ssh 链接右方的复制图标复制该链接：
	![[Pasted image 20250326071538.png]]
	- 切换回命令行，使用 `git remote add` 添加该链接：`git remote add 别名 "链接地址"`
	- 输入命令 `git remote -vv` 可以看到添加的仓库信息
- **使用ssh密钥**
	- 生成密钥：`ssh-keygen -C "comment"`%%可不填写comment%%
	- 获取生成的公钥：找到`.ssh` 文件夹中的`id_rsa.pub`
	- 将公钥配置到 Github
- **提交推送**
	- 添加文件：`git add .`
	- 查看状态：`git status`
	- 提交文件更改：`git commit -m "input yours message"`
	- 推送：`git push -u origin master`
		- origin：这就是上面所说的远程仓库的 “别名”
		- master：代表要推送的分支名称，默认为 master ，可以在 Git Bash 的路径最右端看到。
---

