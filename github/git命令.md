# git 命令

[TOC]

<!-- toc -->

------

参考：http://try.github.io/

commit命令保存的是你的目录下所有文件的快照，就像是把整个目录复制，然后再粘贴一样，但比复制粘贴优雅许多。

```bash
# 提交记录不是挂在当前节点下，而是挂在当前节点的父节点下，即当前节点与提交节点是兄弟关系
git commit --amend
```



```bash
git branch bugFix    # 创建分支
git checkout bugFix  # 切换分支

# 两句变一句
git checkout -b bugFix
```



```bash
git merge bugFix   # 将分支bugFix合并到当前分支上
```


Rebase 实际上就是取出一系列的提交记录，“复制”它们，然后在另外一个地方逐个的放下去。

```bash
# 将当前分支的提交在master基础上再重新提交一遍，当前分支移动到提交后的节点上。
git rebase master   # 把当前分支复制到master分支上（复制的是2者之间不同的节点）
# git rebase master [current_branch]  # 在前一个分支上，将后一个分支上的内容复制过去

git rebase bugFix master  # 将master复制到到bugFix上。
```
rebase优点：Rebase 使你的提交树变得很干净, 所有的提交都在一条线上。

rebase缺点：Rebase 修改了提交树的历史。



分离HEAD

```bash
git checkout c2    # c2 是一个节点的hash值

cat .git/HEAD      # 查看HEAD的指向
git symbolic-ref HEAD   # 如果 HEAD 指向的是一个引用，使用该命令查看它的指向
```


使用节点的hash值不方便，因此可以使用分支名的相对引用：

- 使用 `^` 向上移动 1 个提交记录。
- 使用 `~<num>` 向上移动多个提交记录，如 `~3`。

```bash
git checkout master^   # 将HEAD切换到master的父节点

git checkout HEAD^   # 将HEAD切换到当前HEAD的父节点
```
操作符 `^` 后面也可以跟一个数字，用于指定合并提交记录中的某个父提交。Git 默认选择合并提交的“第一个”父提交，在操作符 `^` 后跟一个数字可以改变这一默认行为。

```bash
# 假定当前master是merge得到的，即当前master有2个父提交

git checkout master^   # HEAD 切换到master的第一个父提交
git checkout master^2  # HEAD 切换到master的第二个父提交

# 支持链式操作
git checkout HEAD~^2~2  # 先到父节点，在到第二个父节点，再到祖节点
```





`-f` 允许许我们将分支强制移动到某个位置。

```bash
git branch -f master HEAD~3   # 强制移动分支master到HEAD的 3 级父提交节点。
```


主要有两种方法用来撤销变更： `git reset`、 `git revert`。

* `git reset` 通过把分支记录回退几个提交记录来实现撤销改动。你可以将这想象成“改写历史”。`git reset` 向上移动分支，原来指向的提交记录就跟从来没有提交过一样。但是这种“改写历史”的方法对大家一起使用的远程分支是无效的。
*  `git revert`用于需要对远程仓库进行撤销的操作。

```bash
git  reset  HEAD~1  # 将当前分支会回退到上一次提交。

git revert HEAD     # 通过新增操作来抵消HEAD节点的增删改，会在HEAD后再新增一个节点。
```


将一些提交复制到当前所在的位置（`HEAD`）下面：

```bash
git cherry-pick <提交号> <提交号> ...
```
如果不清楚想要的提交记录的哈希值时，可以使用交互式的 rebase命令实现cherry-pick功能。

交互式 rebase 指的是使用带参数 `--interactive` 的 rebase 命令, 简写为 `-i`。

可以做3件事：

1. 调整提交记录的顺序。
2. 删除你不想要的提交。
3. 合并提交。允许你把多个提交记录合并成一个。

```bash
git rebase -i HEAD^4  # 从当前HEAD开始往上算，第5个节点处会重新生出一条分支，将前4个节点重新排列或删除。

git rebase -i master  # 将从HEAD到master（不包含master）的节点重新排列提交，在master下生出新分支。
```
`git tag` 可以（在某种程度上，因为标签可以被删除后重新在另外一个位置创建同名的标签）永久地将某个特定的提交命名为里程碑，然后就可以像分支一样引用了。

```bash
git tag tag1 c1  # c1节点上打上标签tag1
git tag tag2     # 在当前HEAD节点上打上标签tag2
```
由于标签在代码库中起着“锚点”的作用，Git 还为此专门设计了一个命令用来**描述**离你最近的锚点（也就是标签），它就是 `git describe`。

Git Describe 能帮你在提交历史中移动了多次以后找到方向。

```bash
git describe <ref>   # <ref> 可以是任何能被 Git 识别成提交记录的引用。不指定时为HEAD。

# 输出结果
# <tag>_<numCommits>_g<hash>
# tag 表示的是离 ref 最近的标签， numCommits 是表示这个 ref 与 tag 相差有多少个提交记录， hash 表示的是你所给定的 ref 所表示的提交记录哈希值的前几位。
# 当 ref 提交记录上有某个标签时，则只输出标签名称
```
## 远程分支

本地仓库会有一个名为 `o/master` 的分支, 这种类型的分支就叫**远程**分支。由于远程分支的特性导致其拥有一些特殊属性。

远程分支反映了远程仓库（在你上次和它通信时）的**状态**。这会有助于你理解本地的工作与公共工作的差别， 这是你与别人分享工作成果前至关重要的一步.

远程分支有一个特别的属性，在你checkout操作时会自动进入分离 HEAD 状态。Git 这么做是出于不能直接在这些分支上进行操作的原因, 你必须在别的地方完成你的工作, （更新了远程分支之后）再用远程分享你的工作成果。

远程分支有一个命名规范：`<remote name>/<branch name>`

如果你看到一个名为 `o/master` 的分支，那么这个分支就叫 `master`，远程仓库的名称就是 `o`

大多数的开发人员会将它们主要的远程仓库命名为 `origin`，并不是 `o`。这是因为当你用 `git clone` 某个仓库时，Git 已经帮你把远程仓库的名称设置为 `origin` 了。

`o/master` 只有在远程仓库中相应的分支更新了以后才会更新。

### fetch

从远程仓库获取数据：`git fetch`。可以将 `git fetch` 的理解为单纯的下载操作。

`git fetch` 完成了仅有的但是很重要的两步：

- 从远程仓库下载本地仓库中缺失的提交记录。
- 更新远程分支指针（如 `o/master`）。

`git fetch` 实际上将本地仓库中的远程分支更新成了远程仓库相应分支最新的状态。`git fetch` 并不会改变你本地仓库的状态。它不会更新你的 `master` 分支，也不会修改你磁盘上的文件。

### pull

`git pull` 等价于下面两条命令：


```bash
git fetch
git merge o/master  # 如果还有其他分支，继续合并。
```



### push

与 `git pull` 相反的命令是`git push`。

`git push` 负责将**你的**变更上传到指定的远程仓库，并在远程仓库上合并你的新提交记录。一旦 `git push` 完成, 你的朋友们就可以从这个远程仓库下载你分享的成果了。

注：`git push` 不带任何参数时的行为与 Git 的一个名为 push.default 的配置有关。



当远程分支有更新时，此时`git push`会有冲突，使用如下方法解决：

```bash
git fetch
git rebase o/master  # 或者 git merge o/master
git push


git pull --rebase  # fetch 和 rebase 的简写。
```

### pull 与 push

本地与远程之间的关联：

- pull 操作时, 提交记录会被先下载到 o/master 上，之后再合并到本地的 master 分支。隐含的合并目标由这个关联确定的。
- push 操作时, 我们把工作从 `master` 推到远程仓库中的 `master` 分支(同时会更新远程分支 `o/master`) 。这个推送的目的地也是由这种关联确定的。

`master` 和 `o/master` 的关联关系就是由分支的“remote tracking”属性决定的。`master` 被设定为跟踪 `o/master` —— 这意味着为 `master` 分支指定了推送的目的地以及拉取后合并的目标。

有两种方法设置这个属性：

1. 第一种就是通过远程分支checkout出一个新的分支，执行`git checkout -b totallyNotMaster o/master`，就可以创建一个名为 `totallyNotMaster` 的分支，它跟踪远程分支 `o/master`。
2. `git branch -u o/master foo` ，这样 `foo` 就会跟踪 `o/master` 了。如果当前就在 foo 分支上, 还可以省略 foo。



push语法：

1. `git push <remote> <place>`
2. `git push origin <source>:<destination>` ： 将本地的source分支推送到远程的destination分支。
   * 如果要推送到的目的分支不存在，Git 会在远程仓库中根据你提供的名称帮你创建这个分支。

```bash
# 切到本地仓库中的“master”分支，获取所有的提交，再到远程仓库“origin”中找到“master”分支，将远程仓库中没有的提交记录都添加上去。
git push origin master
# 通过“place”参数来告诉 Git 提交记录来自于 master, 要推送到远程仓库中的 master。它实际就是要同步的两个仓库的位置。
```

`git fetch` 的参数和 `git push` 极其相似。他们的概念是相同的，只是方向相反罢了。

```bash
git fetch origin foo  # Git会到远程仓库的foo分支上，获取所有本地不存在的提交，放到本地的 o/foo 上。

```

如果 `git fetch` 没有参数，它会下载所有的提交记录到各个本地的远程分支。

省略参数：

* `git push origin :side`：删除远程仓库中的 `side` 分支，相当于将null推送到了远程的side分支。
* `git fetch origin :bugFix`：会在本地创建一个新分支bugFix。



pull：

* `git pull origin foo` 相当于`git fetch origin foo; git merge o/foo`。
* `git pull origin bar~1:bugFix` 相当于`git fetch origin bar~1:bugFix; git merge bugFix`

## 一些小技巧

### .gitignore文件不起作用

在开发过程中，在 `.gitignore`中添加了一些忽略 项，但仍会被提交。

原因：新建的文件在git中会有缓存，如果某些文件已经被纳入了版本管理中，就算是在.gitignore中已经声明了忽略路径也是不起作用的，这时候我们就应该先把本地缓存删除，然后再进行git的push，这样就不会出现忽略的文件了。

命令如下：

```bash
git rm -r --cached .   # -r是递归删除， --cache只从索引中删除，不删除本地文件
git add .
git commit -m 'update .gitignore'
```

### git commit之后想撤销

```bash
git reset --soft HEAD^    # --soft表示只重置HEAD，--hard则重置HEAD，索引，工作树
```

仅仅是撤回commit操作，写的代码仍然保留。

不删除工作空间改动代码，撤销commit，不撤销git add .

### commit注释写错

只是想改一下注释，只需要： `git commit --amend`

## 将当前分支上修改的东西转移到新建分支

比如我在A分支做了一些修改，现在由于某种原因(如A分支已经合并到master)，不能把A分支上修改的东西保留下来但是需要把A分支上修改的东西继续在新分支继续修改。那么现在我们可以有两种简单的做法完成这一需求。

1. 我们不需要在A分支做commit，只需要在A分支新建B分支，然后切换过去。这个时候你会发现修改的东西在A，B分支都有。这个时候在B分支commit，那么这些修改保留在B分支上，再切换到A分支上会发现修改都没有保留下来。
2. 使用`git stash` 将A分支暂存起来，然后在某一个分支（如master分支）新建一个分支B，然后在B分支上使用 `git stash pop` 将修改弹出到B分支上，然后这些修改就在B分支上了。





## 本地新建分支推送到远程仓库

```bash
git checkout -b new_branch
git push --set-upstream origin new_branch
```



## 创建sub-module

子模块允许你将一个 Git 仓库作为另一个 Git 仓库的子目录。 它能让你将另一个仓库克隆到自己的项目中，同时还保持提交的独立。

在父仓库目录下执行以下命令, 将某个子仓库克隆下来，放在sub_module目录下。

```bash
git submodule add https://xxx.git sub_module
```

成功执行上条命令后，会在父仓库根目录下生成一个 `.gitmodules` 文件，里面是一些对子仓库的描述信息。

此外，查看`.git/config`配置文件，可以发现submodule的香港 配置。



如果要克隆一个带有子仓库的仓库，子项目不会自动随父项目克隆出来，需要在父项目克隆下来之后，执行以下命令：

```bash
# 用来初始化本地配置文件
git submodule init
# 从该项目中抓取所有数据并检出父项目中列出的合适的提交(指定的提交)。
git submodule update

#以上两条命令也可以合并成一条组合命令
git submodule update --init --recursive

# clone 父仓库的时候加上 --recursive，会自动初始化并更新仓库中的每一个子模块
```



```bash
# 不加 --remote 会切换到 .submodule 里记录的 SHA1 所在的 commit 节点，加 --remote 则会切换到 submodule 里定义的追踪的分支，默认是 master。
git submodule update --remote
```



## 查看某次commit的内容

```bash
git log  # 展示该分支上的所有提交的commit_id和comment

git show commit_id  # 查看某次commit的内容

git blame -L 10,20 file_name  # 查看某文件的第10到20行的提交历史
```



```bash
# 删除某个本地分支
git branch -D test_branch
```

## 查看某一行代码的修改历史

查看某行代码谁写的：

```bash
git blame file_name
git blame -L 58,100 file_name  # 58~100 行代码
```

其输出格式为：

```bash
commit_ID | 代码提交作者 | 提交时间 | 代码位于文件中的行数 | 实际代码
```

根据 commit_ID 可以查看对应的提交记录：

```bash
git show commit_ID
```



## git拉取指定远程分支

直接拉取：

```bash
git clone -b 远程分支名  仓库地址
```

本地已有相关仓库代码：

```bash
git checkout -b 本地分支 origin/远程分支
```





### git创建新的空分支

```bash
# 该命令会生成一个叫2.0.2的分支，该分支会包含父分支的所有文件。但新的分支不会指向任何以前的提交，就是它没有历史，如果你提交当前内容，那么这次提交就是这个分支的首次提交。
git checkout --orphan 2.0.2

# 移除所有文件
git rm -rf .

# 提交
git commit -m 'new branch'
git push origin 2.0.2
```



## linux的authorized_keys 不生效解决办法

1. .ssh目录必须是700权限
2. authorized_keys 文件必须是600权限

