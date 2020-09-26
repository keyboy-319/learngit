# git 学习

## 建立版本库

在目录下`git init//初始化一个仓库`

## 添加与提交

```git
git add filename//将文件添加到仓库
git commit-m "comment"//提交到仓库，可一次提交多个文件 
```

## 查看状态

`git status`

## 查看版本与回退

### 查看

`git log`

### 回退

`git reset -hard HEAD^`

### 查看命令记录

`git reflog`

### 撤销修改

`git checkout -- file`

撤销回最近一次git add或git commit 后的状态

`git reset HEAD file`

撤销暂存区的修改回工作区

### 从版本库中删除文件

```
rm file//工作区删除
git rm file
git commit//删除库中文件
```

```
git checkout-file//实际上是将版本库中的文件替换工作区的文件，所以无论修改还是删除都可以还原
```

## 链接远程库

```
git remote add origin git@server-name:path/repo-name.git
git push -u origin master//第一次推送时
git push orgin master//第一次后
```

## 先建立远程库再克隆版本库

#### 勾选Initialize this repository with a README,git 就会帮我们建立一个readme.md文件在库中

##### 克隆远程库到本地

`git clone git@github.com:hithub name/file.git `

### **分支管理**

```
git checkout -b dev//创建dev分支
//git checkout -b表示创建并切换，
//相当于git branch dev
//和git checkout dev这两条命令
```

```
然后用git branch查看当前分支
然后可以在dev上提交等操作，git add git commit -m"sth"等
```



```
git checkout master//切换为master 分支
//目前没找到修改的文件是因为文件还在dev分支上
```

```
git merge dev//合并指定分支到当前分支上
```

####更安全的创建分支与切换/switch

```
git switch -c dev//创建并切换到新分支
git switch master//切换分支
```

删除分支

```
git branch -d file
```

查看分支合并图

`git log --graph`

##### 普通模式合并与fast forward合并

```
git merge -no-ff -m"sth" dev //普通模式合并
git merge dev//ff模式合并
//普通模式合并，合并后历史有分支，能看出来曾经做过合并，而ff看不出

```

### 临时保存未完成的文件

```
//当前在f分支干活
git stash//将当前的工作现场保存起来
git checkout master
git checkout -b sth//返回master 建立分支干活，比如修复bug等操作后
git switch f
git stash list//查看之前第二行时储存的工作现场
git stash apply//恢复工作现场但在stash list中不删除
git stash pop//恢复并删除stash list中的现场

```

将master 上修复的bug在f分支上也有时

```
//在f分支上
git cherry-pick commitid//可以将之前的commit 在f分支上重新覆盖

```

##### 强制删除未保存的分支

`git branch -D name`

### 从远程库中获取更新

```
git fetch origin//全部更新
git fetch origin master//master分支更新
//取回更新后会返回一个FETCH_HEAD,指branch在服务器上的最新状态
git log -p FETCH_HEAD//查看更新信息
```

#### 团队协作时

![image-20200926151845809](C:\Users\hasee\AppData\Roaming\Typora\typora-user-images\image-20200926151845809.png)