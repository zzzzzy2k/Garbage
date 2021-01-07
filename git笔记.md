# Git笔记

## 创建代码仓库

配置身份

```
git config --global user.name "zzzzzy2k"
git config --global user.email "810256499@qq.com"
```

在空的文件夹里面创建代码仓库

```
git init
```

## 提交本地代码

先创建一个readme.txt，在里面随便写点东西

```
git add readme.txt
git commit -m "Hello Git"
```

可以add多个文件后再依次性commit

```
git add .
```

我们可以在代码仓库的根目录下创建一个名为.gitignore的文件，然后编辑里面的内容，把不需提交的文件忽略掉！

编辑内容为

```
/gen/
/bin/	//不需要提交的文件名
project.properties
```

## 查看修改内容

使用git status可以查看 修改的部分，查看状态

```
git status
```

它会提示我们哪些文件发生了改变，但是还没有提交，如果想看具体更改了什么可以用一下命令。按q可以退出命令行输入！

```
git diff
```

> git diff比较的是工作目录中当前文件和暂存区域快照之间的差异， 也就是修改之后还没有暂存起来的变化内容。若要查看已暂存的将要添加到下次提交里的内容，可以用 git diff --cached 命令。
>
> 请注意，git diff 本身只显示尚未暂存的改动，而不是自上次提交以来所做的所有改动。 所以有时候你一下子暂存了所有更新过的文件后，运行 git diff 后却什么也没有，就是这个原因。

> Git管理的文件分为：工作区，版本库，版本库又分为暂存区stage和暂存区分支master(仓库)
>
> 工作区>>>>暂存区>>>>仓库
>
> git add把文件从工作区>>>>暂存区，git commit把文件从暂存区>>>>仓库，
>
> git diff查看工作区和暂存区差异，
>
> git diff --cached查看暂存区和仓库差异，
>
> git diff HEAD 查看工作区和仓库的差异，
>
> git add的反向命令git checkout，撤销工作区修改，即把暂存区最新版本转移到工作区，
>
> git commit的反向命令git reset HEAD，就是把仓库最新版本转移到暂存区。

## 查看提交记录

```
git log
```

可以用以下命令只查看提交对应的版本号以及commit的内容。

```
git log --pretty=online
```

## 撤销未提交的修改

还没有add的时候

git diff 可以查看改变的内容

```
git checkout [src/com/jay/example/testforgit/MainActivity.java]
```

[]里的内容是文件地址

如果已经add了，checkout是没有作用的，我们要先取消添加才可以撤回提交，使用下述指令：

```
git reset HEAD src/com/jay/example/testforgit/MainActivity.java
git checkout src/com/jay/example/testforgit/MainActivity.java
```

## 版本回退

git log可以查看我们的提交记录，我们需要从这里获取一个版本号， 一般我们只需要前七位字符就够了；在Git中，用**HEAD**代表当前版本，上一个版本就是**HEAD^**， 再上一个版本就是**HEAD^^**依次类推！我们先Git Log看下版本历史先！

回到前一个版本的命令：

```
 git reset --hard HEAD
 git reset --hard HEAD^
 git log
```

当然也可以直接根据版本号回退

```
git reset --hard ad2080c
```

如果后悔了，想要回退回新的版本，git log却没有了最新的那个版本号，这时可以根据以下命令恢复：

```
git reflog
```

可以发现版本号的出现

然后再键入：

```
git reset --hard ad2080c
```