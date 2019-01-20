# Git使用总结

## 1.安装

**Linux:** `sudo apt isntall git`

**Windows:** 浏览器打开[git for windows](https://git-scm.com/download/win)，按照系统位数下载对应安装程序，安装即可。

**MacOS:** 浏览器打开[git for mac](https://git-scm.com/download/mac)，下载安装程序，安装即可。

## 2.创建新仓库

命令行进入目标文件夹，执行`git init`以创建新的 git 仓库。

## 3.工作流

本地仓库由 git 维护的三部分组成。第一部分是当前工作目录，它持有实际文件；第二个是缓存区（Index），它是个缓存区域，临时保存改动；最后是HEAD，指向最近一次提交后的结果。

## 4.添加与提交

可以使用如下命令将工作目录的改动添加到缓存区：

```
git add <filename>
git add *
```

使用如下命令将缓存区以实际提交改动：

```
git commit -m "commit info"
```

## 5.推送改动到远端仓库

使用如下命令添加远端仓库：

```
git remote add origin <server>
```

此时可以将改动推送到所添加的服务器上：

```
git push origin master
```

## 6.分支管理

![](../resources/git_branch.png)

+ 查看分支列表：

```
git branch
```

+ 新建分支：

```
git branch <branchname>
```

+ 切换分支：

```
git checkout <branchname>
```

+ 新建并切换分支：

```
git branch -b <branchname>
```

+ 合并分支（如合并到master）：

```
git checkout master
git merge <branchname>
```

+ 删除分支

```
git branch -d <branchname>
```

