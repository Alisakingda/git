# Git

## 版本控制系统（version control system）

## 分布式版本控制系统，所以每个机器都必须自报家门：用户名和电子邮箱地址

```js
$ git config --global user.name "your name"
$ git config --global user.email "your email"
```

```js
// 创建仓库，并添加文件提交;
$ git init
$ git add .
$ git commit -m "description"

// 修改
$ git status
$ git diff  // 查看区别(difference)
$ git add .
$ git commit -m "update description"

// 版本回退
$ git log -3  // 查看提交日志
$ git reset --hard HEAD^  // 上一个版本
$ git reset --hard HEAD^^ // 上上个版本
$ git reset --hard HEAD-n // n个版本
$ git reset --hard 7ff439fd06d3fab75662fc753e92dd4f9affdff4  //到指定版本

// git提供 `git reflog`用来记录每一次命令
$ git reflog

// 工作区  暂存区（stage） 版本库

// 撤销更改
$ git checkout <file>  // 没有git add .
// 如果git add .
$ git reset HEAD <file>
$ git checkout <file>

// 删除文件
$ git rm <file>
// 存在误删，请从版本库里面恢复，$ git reset --hard <哈希值>

// 连接远程仓库(已有的)
$ git remote add origin <resp> // 连接远程已有的仓库
$ git push origin <resp>
$ git push
$ git pull

// 从远程仓库克隆
$ git clone <resp>

// 分支branch
$ git checkout -b dev // 创建并切换到dev分支
$ git branch  // 查看本地分支
1. $ git add .
2. $ git commit -m "dev test"
3. $ git checkout master
4. $ git merge dev // 将dev中的代码合并到主干上
$ git branch -a // 查看所有分支，包括远程上的branch
$ git branch -D dev // 删除分支(销毁)

// 解决冲突
// git用 <<<<<<<、========、>>>>>>> 来标记不同分支的内容，手动删除，保存并commit,then push;

// 分支管理策略
// 通常情况下，合并分支，git会用fast forward 模式，删除分支后，会丢掉分支信息
$ git merge --no-ff -m 'info' dev   // git merge dev

// master 分支应当是非常稳定的，干活在dev上，每个人都有自己的分支开发

// bug修改
$ git stash // 暂存（储藏）
$ git stash list // 查看暂存区状态
$ git pop // 取
$ git stash list

// feature（功能分支）

// 多人协作
// 查看远程库的信息
$ git remote
$ git remote -v

$ git push origin master
$ git push origin dev

// 提交之前，先从远程pull $ git pull
$ git branch --set-upstream-to=origin/dev dev  // 将远程的dev与本地的dev连接起来

// 多人协作开发的工作模式
1. 建立自己的远程分支，推送自己的更改，$ git push origin <branch name>
2. $ git pull
3. 合并有冲突，解决冲突;
4. $ git push origin <branch name>

// git pull 提示 no tracking information ,则说明本地分支与远程分支没有链接

// 多人在同一分支协作开发，很容易冲突，log日志也会变得很凌乱
$ git log --graph --pretty=oneline --abbrev-commit
$ git rebase // 变基

// 标签管理
$ git tag v1.0  // 打标签
$ git tag  // 查看所有标签
$ git show <tagname> // 查看tag说明文字
$ git tag -d v1.0 // 删除标签(仅删除本地)
$ git push origin v1.0

// 删除远程tag
$ git tag -d v1.0
$ git push origin -d tag v1.0
```
