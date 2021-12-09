## git 学习

#### git status

要查看哪些文件处于什么状态，可以用 `git status` 命令。 如果在克隆仓库后立即使用此命令，会看到类似这样的输出

#### git remote

列出你指定的每一个远程服务器的简写

origin - 这是 Git 给你克隆的仓库服务器的默认名字

#### git branch

`git branch` 可以创建与删除分支。 如果不加任何参数运行它，会得到当前所有分支的一个列表：

`-v`查看每一个分支的最后一次提交

`-a`查看远程分支，远程分支会用红色表示出来

`git branch testing`创建新分支，不会切换到新的分支

`--merged`查看哪些分支已经合并到当前分支

列表中分支名字前**没有 `*` 号**的分支通常可以使用 `git branch -d` 删除掉

`--no-merged`查看所有包含未合并工作的分支

`-d`删除分支

`-D`强制删除

#### git checkout

`git checkout -- [file]`撤销修改。对文件的任何修改都会消失，拷贝另一个文件覆盖

`git checkout .`撤销工作区当前路径下所有文件的修改

`git checkout testing`切换到已经存在的分支

`-b`运行`git checkout -b iss53`相当于`git branch iss53`和`git checkout iss53`



#### git log

查看提交历史 `git log`会按提交时间列出所有的更新，最近的更新排在最上面

`-p`显示每次提交的内容差异

`-2`来仅显示最近两次提交

`--stat`每次提交的简略的统计信息

#### git add

`git add` 命令来实现对指定文件的跟踪，暂存

#### git init

在现有目录中初始化仓库

#### git diff

[git diff 用法](https://blog.csdn.net/wq6ylg08/article/details/88798254)

`git diff`当工作区有改动，临时区为空，diff的对比是“工作区与最后一次commit提交的仓库的共同文件”；当工作区有改动，临时区不为空，diff对比的是“工作区与暂存区的共同文件”。

`git diff --cached` 或 `git diff --staged`显示暂存区(已add但未commit文件)和最后一次commit(HEAD)之间的所有不相同文件的增删改(git diff --cached和git diff –staged相同作用)

#### git reset

`git reset HEAD <file>`取消暂存某个文件

`git reset HEAD .`取消暂存当前路径下的所有文件

执行commit后还没有push，撤销这次commit

`git reset --soft HEAD^`撤销commit，不撤销add

`git reset --hard HEAD^`撤销commit且撤销add

`HADE^n`取消最近的n次提交

`git reset –soft xxx`回退到某一个版本

`git reset –soft HEAD~1`
回退一个版本,不清空暂存区,将已提交的内容恢复到暂存区,不影响原来本地的文件(未提交的也不受影响)
`git reset –hard HEAD~1`
回退一个版本,清空暂存区,将已提交的内容的版本恢复到本地,本地的文件也将被恢复的版本替换

#### git commit

提交最后一次`git add`命令的那个版本

`git commit --amend`修改最近一次提交的提交信息



#### git filter-branch

`git filter-branch --tree-filter 'rm -f passwords.txt' HEAD`

从整个提交历史中移除，删除有关passwords.txt

#### git rebase

将提交到某一分支上的所有修改都移至另一分支上

#### git stash

将工作区的修改临时保存在储藏区

`git stash pop`

`git stash apply`

将储藏区的内容恢复到工作区

`git stash list`查看储藏区有那些临时修改

`git stash drop stash@{$num}`

`git stash clear`

丢弃储藏区的修改

