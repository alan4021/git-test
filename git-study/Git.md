# Git 2.37.3

## 下载地址

[Git下载地址windows64](https://git-scm.com/download/win)

## 安装

[安装教程](https://zhuanlan.zhihu.com/p/473593640#:~:text=2022%E6%9C%80%E6%96%B0%E8%B6%85%E8%AF%A6%E7%BB%86Git%E5%AE%89%E8%A3%85%E6%95%99%E7%A8%8B%201%20%EF%BC%89%E8%AE%B8%E5%8F%AF%E7%94%B3%E6%98%8E%202%20%EF%BC%89%E9%80%89%E6%8B%A9%E5%AE%89%E8%A3%85%E8%B7%AF%E5%BE%84%203%20%EF%BC%89%E9%80%89%E6%8B%A9%E5%AE%89%E8%A3%85%E7%BB%84%E4%BB%B6%204,%EF%BC%89%E9%80%89%E6%8B%A9https%E4%BC%A0%E8%BE%93%E5%90%8E%E7%AB%AF....%209%20%EF%BC%89%E9%85%8D%E7%BD%AE%E7%BB%93%E6%9D%9F%E8%A1%8C%E8%BD%AC%E6%8D%A2%E6%96%B9%E5%BC%8F....%2010%20%EF%BC%89%E9%85%8D%E7%BD%AE%E7%BB%88%E7%AB%AF%E6%A8%A1%E6%8B%9F%E5%99%A8%E4%B8%BA%E4%BD%BF%E7%94%A8Git%20Bash%20%E6%9B%B4%E5%A4%9A%E7%BB%93%E6%9E%9C...%20)

## 基本使用命令

### 设置用户签名

```
$ git config --global user.name alan
$ git config --global user.email alan@groot.icu
```

### 查看签名

作用：区分不同操作者的身份

C:\Users\Alan4\\.gitconfig

```
[user]
	email = alan@groot.icu
	name = alan
```



### `git status`

作用：显示工作树(本地库)状态

```
$ git status
fatal: not a git repository (or any of the parent directories): .git
```

### `git init`

作用：创建一个空的 Git 存储库或重新初始化现有的

```
$ git init
Initialized empty Git repository in D:/Git/File/test/.git/

$ git status
On branch master(在主分支)
No commits yet(没有需要提交的)
nothing to commit (create/copy files and use "git add" to track)(目前没有需要提交的)

```

### `git add 文件`

作用：将文件添加到暂存区来跟踪文件

当我们将本地库进行修改时(新建一个文件test.txt)

```
$ git status
On branch master

No commits yet

Untracked files:(#没有跟踪的文件)
  (use "git add <file>..." to include in what will be committed(#使用“git add …”来包含要提交的内容))
        test.txt

nothing added to commit but untracked files present (#没有添加要提交的文件，只有未跟踪的文件)(use "git add" to track(#使用git add来跟踪))

$ git add test.txt

$ git status
On branch master

No commits yet

Changes to be committed:(#需要commit的文件)
  (use "git rm --cached <file>..." to unstage)
        new file:   test.txt
```

### `git rm --cached 文件`

作用：删掉暂存区中跟踪的文件

```
$ git rm --cached test.txt
rm 'test.txt'

$ git status
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        test.txt

nothing added to commit but untracked files present (use "git add" to track)
```

### `git commit -m  "日志信息"  文件`

作用：将暂存区的文件提交到本地库

```
$ git commit -m "第一版本" test.txt
[master (root-commit) c10fd33] 第一版本
 1 file changed, 0 insertions(+), 0 deletions(-)(#一个文件被改变，0行被插入，0行被删除)
 create mode 100644 test.txt
 
 $ git status
On branch master(#master分支)
nothing to commit, working tree clean(#已经被提交了，工作树本地库干净没有修改)

```

c10fd33] ：版本号

### `git reflog`

作用：查看版本信息

```
$ git reflog
c10fd33 (HEAD -> master) HEAD@{0}: commit (initial): 第一版本
```

### `git log`

作用：查看详细日志

```
$ git log
commit c10fd33f29138604065f3469877e84ff08cc0e43 (HEAD -> master)
Author: alan <alan@groot.icu>
Date:   Thu Sep 15 15:23:15 2022 +0800

    第一版本
```

c10fd33f29138604065f3469877e84ff08cc0e43 ：完整版本号

### `git  reset --harc 版本号`

```git
Alan4@Alan MINGW64 /d/Git/File/test (master)
# 查看版本信息(head指向master的第三个版本)
$ git reflog
cba2293 (HEAD -> master) HEAD@{0}: commit: 第三个版本
8a00f75 HEAD@{1}: commit: 第二版
c10fd33 HEAD@{2}: commit (initial): 第一版本

Alan4@Alan MINGW64 /d/Git/File/test (master)
# 切换到第二版本
$ git reset --hard 8a00f75
HEAD is now at 8a00f75 第二版

Alan4@Alan MINGW64 /d/Git/File/test (master)
# 查看版本信息(head指向master的第二个版本并记录了移动指针的信息)
$ git reflog
8a00f75 (HEAD -> master) HEAD@{0}: reset: moving to 8a00f75
cba2293 HEAD@{1}: commit: 第三个版本
8a00f75 (HEAD -> master) HEAD@{2}: commit: 第二版
c10fd33 HEAD@{3}: commit (initial): 第一版本
```

### `git remote -v`

查看远程地址的别名

### `git remote add 仓库名 远程链接`

- 给远程链接创建别名，为了简化链接
- fetch可以使用别名
- push可以使用别名



## 分支

### git branch 分支名

创建分支

```
# 创建一个热修复分支
$ git branch hot-fix
```



### git branch -v

查看分支

```
# 就两个分支
$ git branch -v
  hot-fix cba2293 第三个版本
* master  cba2293 第三个版本
```

### git checkout 分支名

切换分支

```
# 切换分支
Alan4@Alan MINGW64 /d/Git/File/test (master)
$ git checkout hot-fix
Switched to branch 'hot-fix'

# 查看分支
Alan4@Alan MINGW64 /d/Git/File/test (hot-fix)
$ git branch -v
* hot-fix cba2293 第三个版本
  master  cba2293 第三个版本
```

## 分支合并

### git merge 分支名

#### 正常合并

将分支合并到当前分支上

```
Alan4@Alan MINGW64 /d/Git/File/test (master)
$ git merge hot-fix
Updating cba2293..5990359
Fast-forward
 test.txt | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)
```

#### 冲突合并

**冲突合并指的是需要合并的两个分支上同一处信息有两个不同的版本，需要人为的干预选择哪个版本**

```
# 合并分支
$ git merge hot-fix
Auto-merging test.txt
CONFLICT (content): Merge conflict in test.txt
Automatic merge failed; fix conflicts and then commit the result.(自动合并失败;修复冲突，然后提交结果。)
Alan4@Alan MINGW64 /d/Git/File/test (master|MERGING) # 指的是正在合并中

# 查看状态
$ git status
On branch master
You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Unmerged paths:
  (use "git add <file>..." to mark resolution)
        both modified(# 两个修改):   test.txt

no changes added to commit (use "git add" and/or "git commit -a")
```

##### 查看文件

```
<<<<<<< HEAD
432156789、-----。
=======
324156789、++++++。
>>>>>>> hot-fix
```

- <<<<<<<：当前分支
- ======：上面的为当前分支修改的代码
- />>>>>>>>：需要合并的另一个分支

##### 人为干预版本

- **将需要的信息保存，不需要的信息删除，然后再删除<<<<、=====、>>>>>>这三行**
- 然后git add test.txt 添加暂存区
- 然后提交git commit -m "合并冲突"   注意：不能加文件名字

## 团队合作

### 

## GitHub

### github创建远程仓库

#### 第一步

![image-20221009145413047](.\new-repository)

#### 第二步

![image-20221009172642740](.\create-repository)

#### 第三步

![image-20221009172829423](.\clone-repository-url)

### 创建别名

