# git

版本控制工具

集中式svn,分布式git；svn已被git淘汰

集中式优点：代码放在单一的服务器上，便于项目的管理。缺点：服务器宕机：员工写的代码得不到保障；服务器炸了：整个项目的历史记录都没了。

分布式就是去中心化，区块链的思想

git每次存的都是完整的版本，但是经过压缩算法比svn也没多多少。git的回滚速度非常快。

github相当于分布式版本控制的中央服务器。

区域：工作区、暂存区、版本库

对象：git对象、树对象、提交对象

windows中查看可以设置隐藏目录

git init初始化目录

linux中find命令可以查看文件夹下的文件

git对象是键值对，key是value对应的哈希

 ***git hash-object -w ./test.txt 存储内容***

***$ git cat-file -p c31fb1e89d8b6b3ef34cdb5a2f999d6e29b822ba 查看内容***

# Git 基本操作

Git 常用的是以下 6 个命令：**git clone**、**git push**、**git add** 、**git commit**、**git checkout**、**git pull**

![img](https://www.runoob.com/wp-content/uploads/2015/02/git-command.jpg)

- workspace：工作区
- staging area：暂存区/缓存区
- local repository：版本库或本地仓库
- remote repository：远程仓库



# git工作步骤

1、进入要管理的文件夹（进入）

2、初始化（提名）    git init

3、管理    git status    git add index.html    git add .   

个人信息配置：用户名、邮箱

4、生成版本     git commit -m '描述信息 '    git log

三种状态的变化：红色，新增的文件/修改了老文件；绿色，git已经管理起来；生成版本

# git三大区域

工作区、暂存区、版本库

工作区：已管、新/修

git log               git log --graph



# git回滚

git reset --hard  05152f4a0551ed95cb4db83cc5bf0e402fc212d0(版本号)

git reflog

# git分支

主干 master

分支 branch    每个分支相当于一个隔离的环境

合并 merge

git branch（查看分支）    git branch 分支名（创建分支）   git checkout 分支名（切换分支）   git branch -d 分支名（删除分支）

git merge 分支名（合并分支）    合并分支可能产生冲突

git工作流  开发时至少有两个分支，一个master分支，一个dev分支；master正式，dev开发

bug分支

# rebase

使git记录简洁

多个记录整合成一个记录

git rebase -i HEAD~3

# Git 远程仓库(Github)

Git 并不像 SVN 那样有个中心服务器。

目前我们使用到的 Git 命令都是在本地执行，如果你想通过 Git 分享你的代码或者与其他开发人员合作。 你就需要将数据放到一台其他开发人员能够连接的服务器上。

![img](https://www.runoob.com/wp-content/uploads/2015/03/Git-push-command.jpeg)

## Github 简明教程

注册账号、创建仓库、本地代码推送

```git
给远程仓库起别名为origin   上传代码
git remote add origin https://github.com/Pengbr/gitExercise.git
git push -u origin master

拉取代码
git clone https://github.com/Pengbr/gitExercise.git   第一次
git pull origin master
```

 vim .git/config  修改git配置文件

github token   github访问令牌token

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

# 多人协同开发

gitflow工作流    review    release

github创建组织，多人协同开发

git tag -a v1 -m "第一版"   给冗长的哈希值打一个tag标签

代码review   pull request

给开源项目贡献代码  fork    pull request

gitignore忽略文件    让git不再管理当前目录下的某些文件
