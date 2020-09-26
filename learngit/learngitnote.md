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



