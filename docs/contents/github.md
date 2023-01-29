# 参考

https://git-scm.com/book/zh/v2



# github简单流程

#### 初始化

```bash
vim main.c #编辑文件，随便都行
#写上一些语句
ls

git init
dir -h

#文件目录创建了.git目录，创建了（Index，Hostory区域）

#配置全局用户名和邮件，针对单独存储库就用 --local

git config --global user.name "xxxxx-xxxx"
git config --global user.email "xxxxx@xxxx.com"

git config --global core.autocrlf true #window与linux的行尾不一样

git config --list

git status
On branch master
No commits yet
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        main.c
nothing added to commit but untracked files present (use "git add" to track)
#告知我们可以将main.c放进暂存区（Index区域）

```



#### 添加追踪

```bash
git add main.c
git status
On branch master
No commits yet
Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   main.c
```

#### 第一次提交

```bash
git commit -m "add main.c"
[master (root-commit) 394ce40] add main.c
 1 file changed, 13 insertions(+)
 create mode 100644 main.c
```



#### 回顾第一次操作

```bash
#编辑文件
vim main.c #编辑文件，随便都行

#跟踪文件
git add main.c

#提交
git commit -m "add main.c"

#查看状态 已经没有更改的文件，在文件树
git status
On branch master
nothing to commit, working tree clean


```



#### 查看提交记录

```bash
git log
commit 394ce404b2520b98e4eb9eb04102ce739157986c (HEAD -> master)
Author: arbin-ruisen <ruisen_pan@arbin.com>
Date:   Sun Jan 29 10:34:42 2023 +0800

    add main.c
```



#### 添加新文件，区域状态

```bash
#添加新文件
cp main.c main2.c
#随便修改main.c和main2.c

git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   main.c

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        main2.c
        
#文件树里存在main.c和main2.c, 未进行跟踪的有main2.c ,在Index区域还保留旧的main.c, github得知 main.c进行了修改

git diff #查看文件差异

#git add main.c main2.c 不使用
#git add main*.c
git add .  #所有新文件和修改文件都添加到暂存（Index区域）

git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   main.c
        new file:   main2.c
#文件树和暂存区都是同样的文件内容了

git diff --staged #显示暂存区和最近的commit之间的区别

git commit -m "add main2.c and edit main.c" #第二次提交

git log -p #显示提交内容差异

```



#### 添加新文件，区域状态

```bash
git rm main.c
git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        deleted:    main.c
#感知到main.c从文件树删除 删除的操作被暂存了

git config --global core.editor vim #上网搜对应编辑器

git commit #打开默认编辑器
```



#### 撤销文件树的更改

```bash
vim main2.c
git diff

git checkout -- main2.c #无法找回了！

git diff
git status
```



#### 取消文件在暂存（Index区域）内

```bash
vim main2.c
git add main2.c
git diff 
git diff --staged #暂存区和最近提交区别
git reset HEAD main2.c #最新提交里恢复暂存的main2.c
git status
git checkout -- main2.c #恢复文件树的内容
```



#### 从先前的提交恢复文件

```bash
git log -- main.c #查看main.c相关的提交
git checkout 4ba96f2 -- main.c #从4ba96f2获取main.c
git status
git commit -m "resotre main.c"
```



#### 排除文件

```bash
#不想让git跟踪，排除特定文件夹或者二进制文件
vim .gitignore


```



对比工具设置（C:\Users\xxxx\.gitconfig）

```bash
[diff]
tool = bc4
[difftool]
prompt = false
[difftool "bc4"]
cmd = "\"C:/soft/BCompare/BCompare.exe\" \"$LOCAL\" \"$REMOTE\""
[merge]
tool = bc
[mergetool]
prompt = false
[mergetool "bc4"]
cmd = "\"C:/soft/BCompare/BCompare.exe\" \"$LOCAL\" \"$REMOTE\" \"$BASE\" \"$MERGED\""
```

#### 

#### 分支

```bash
#分支允许并行处理文件

git log --oneline
git branch b1
git branch b2
#git checkout -b b2 创建并切换到b2分支

git checkout b1 #切换到b1分支

vim main.c #随便修改
git diff
git add .
git commit -m "b1 modifted"

git checkout b1 #切换到b2分支
vim main.c #随便修改
git diff
git commit -a -m "b2 modifted"

git config --global alias.grap 'log --oneline --all --graph'
git log --oneline --all --graph

```



#### 合并（前向合并）

```bash
git checkout master
git diff master..b1 #git difftool master..b1
git merge b1
```



#### 删除分支

```bash
git branch --merged #查看哪些分支已经合并到当前分支
git branch -d b1
git branch -d b2 #会提示失败，因为没合并
```



#### 合并（三向合并）

```bash
git checkout master
git merge b2
git status
#合并完毕后
git add .
git commit 
```



#### HEAD指针

```bash
#HEAD指向某个commit
git checkout 87eae2 
git checkout master #回到分支上

#HEAD~1指回退一个快照 简写为HEAD~
#HEAD~2指回退两个快照
#当有多个父级提交会更复杂，直接使用commit hash

```



#### 多处理

```bash
#修改了文件后，不add, 无法跳转分支
git checkout master
git branch dev
vim main.c
git commit -a -m "test jump to dev"
vim main.c
git checkout dev #无法跳转
git stash push -m "test"
git stash list -p
git stash apply #应用最新的 或者指定'stash@{0}'
git stash drop 'stash@{0}'
```



#### 重置了解

```bash
git reset --soft HEAD~2 #回退2个提交，回退的代码都会放在暂存区
git reset --mixed HEAD~2 #回退2个提交，回退的代码都会放在文件树
git reset --hard HEAD~2 #回退2个提交，清空工作目录及暂存区所有修改
```



#### 远程

```bash
git remote
git remote -v
git remote remove
git pull #git fetch git merge 组合成

git remote add upstream #address
```

