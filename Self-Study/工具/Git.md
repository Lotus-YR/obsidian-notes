参考文章：[廖雪峰GIT教程](https://liaoxuefeng.com/books/git/introduction/index.html)
# git
分布式版本控制系统

集中式：版本库存放在中央服务器，必须联网
分布式：版本库在自己电脑，中央服务器用于交换代码

所有的版本控制系统，其实只能**跟踪文本文件的改动**（word文件是二进制格式 不行）

# 下载安装
下载链接：[[https://git-scm.com/downloads]]

安装完成后进行配置
```plain
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
```

# 创建版本库
版本库
=仓库（repository）
=一个目录，其中所以文件都可以被git管理

1. 适合地方创建空目录，也可以选有东西的目录
2. 通过`git init`命令把这个目录变成Git可以管理的仓库

### 添加文件到版本库
1. 用命令`git add`告诉Git，把文件添加到仓库
2. 用命令`git commit`告诉Git，把文件提交到仓库
	```
	$ git commit -m "xxxxx"
	```
	-m 后面输入的是本次提交的说明，可以是任意内容，最好有意义，方便查找改动记录
	commit一次性可以提交很多文件，可以多次add不同文件后一次提交

# 时光穿梭机
`git status`命令可以让我们时刻掌握仓库当前的状态
`git diff`顾名思义就是查看difference，显示的格式正是Unix通用的diff格式

### 版本回退
在Git中，我们用`git log`命令查看历史版本（提交）记录
`git log`命令显示从最近到最远的提交日志

看到的一大串类似`1094adb...`的是`commit id`（版本号），和SVN不一样，Git的`commit id`不是1，2，3……递增的数字，而是一个SHA1计算出来的一个非常大的数字，用十六进制表示。
为什么`commit id`需要用这么一大串数字表示呢？因为Git是分布式的版本控制系统，后面我们还要研究多人在同一个版本库里工作，如果大家都用1，2，3……作为版本号，那肯定就冲突了。

把当前版本`append GPL`回退到上一个版本`add distributed`，就可以使用`git reset`命令
```plain
$ git reset --hard HEAD^
HEAD is now at e475afc add distributed
```
`--hard`会回退到上个版本的已提交状态，而`--soft`会回退到上个版本的未提交状态，`--mixed`会回退到上个版本已添加但未提交的状态。

指定回到未来的某个版本：
```plain
$ git reset --hard 1094a
HEAD is now at 83b0afe append GPL
```
版本号没必要写全，前几位就可以了，Git会自动去找。当然也不能只写前一两位，因为Git可能会找到多个版本号，就无法确定是哪一个了。

Git提供了一个命令`git reflog`用来记录你的每一次命令，即使关闭电脑后也可以恢复到未来的版本（找到commit id即可）

**让`HEAD`指向哪个版本号，你就把当前版本定位在哪**

### 工作区和暂存区
工作区：电脑里能看到的目录
版本库：工作区中的隐藏目录`.git` 
	版本库中最重要的就是称为stage（index）的**暂存区**和git为自动创建的第一个分支`master`，以及指向master的一个指针`HEAD`
	![[Pasted image 20241127154015.png|300]]

`git add`命令实际上就是把要提交的所有修改放到暂存区（Stage），然后，执行`git commit`就可以一次性把暂存区的所有修改提交到分支

### 管理修改
Git跟踪并管理的是修改，而非文件
每次修改，如果不用`git add`到暂存区，那就不会加入到`commit`中

### 撤销修改
`git checkout -- file`可以丢弃工作区的修改
就是让这个文件回到最近一次`git commit`或`git add`时的状态

用命令`git reset HEAD <file>`可以把暂存区的修改撤销掉（unstage），重新放回工作区

### 删除文件
删除文件后，`git status`会显示被删除的文件
- 确实要删除：`git rm` + `git commit` 从版本库中删除
- 删错了：`git checkout --file` 恢复

>从来没有被添加到版本库就被删除的文件是无法恢复的

# 远程仓库
本地Git仓库和GitHub仓库之间的传输是通过**SSH加密**的
- 创建SSH Key：主目录下查看.ssh目录，查看目录中是否有id_rsa和id_rsa.pub这两个文件，有则不用创建。没有，则打开Git Bash，输入`$ ssh-keygen -t rsa -C "youremail@example.com"` 
- 登录GitHub，添加SSH Keys

### 添加远程仓库
1. 在GitHub上新建仓库
2. 在本地仓库下运行命令：`$ git remote add origin git@github.com:USER_NAME/REPO_NAME.git`
	@后面是远程仓库的链接 也可以是`https://github.com/xxxx`这种形式
	`origin`是远程库的名字，git的默认叫法，也可以改成别的
3. 使用`git push`命令，把当前分支master推到远程
	第一次推送分支时加上`-u`参数，可以把本地master分支和远程master分支关联起来

##### SSH警告
当你第一次使用Git的`clone`或者`push`命令连接GitHub时，会得到一个警告：
```plain
The authenticity of host 'github.com (xx.xx.xx.xx)' can't be established.
RSA key fingerprint is xx.xx.xx.xx.xx.
Are you sure you want to continue connecting (yes/no)?
```
这是因为Git使用SSH连接，而SSH连接在第一次验证GitHub服务器的Key时，需要你确认GitHub的Key的指纹信息是否真的来自GitHub的服务器，输入`yes`回车即可

##### 删除远程仓库
如果添加的时候地址写错了，或者就是想删除远程库，可以用`git remote rm <name>`命令
使用前，建议先用`git remote -v`查看远程库信息

删除只是解除绑定关系，没有物理上删除远程仓库
要真正删除远程仓库，需要登录到GitHub，后台页面删除

### 从远程仓库克隆
之前是先有本地库，后有远程库，关联二者
现在是先建远程库，从远程库克隆到本地

1. 创建远程库
2. 在本地库使用命令`git clone`克隆

GitHub给出的地址不止一个，还可以用`https://github.com/michaelliao/gitskills.git`这样的地址。实际上，Git支持多种协议，默认的`git://`使用`ssh`，但也可以使用`https`等其他协议。
使用`https`除了速度慢以外，还有个最大的麻烦是每次推送都必须输入口令，但是在某些只开放`http`端口的公司内部就无法使用`ssh`协议而只能用`https`。

# 分支管理※
你创建了一个属于你自己的分支，别人看不到，还继续在原来的分支上正常工作，而你在自己的分支上干活，想提交就提交，直到开发完毕后，再一次性合并到原来的分支上，这样，既安全，又不影响别人工作。

### 创建与合并分支
截止到目前，只有一条时间线，在Git里，这个分支叫主分支，即`master`分支。`HEAD`严格来说不是指向提交，而是指向`master`，`master`才是指向提交的，所以，`HEAD`指向的就是当前分支。

每次提交，`master`分支都会向前移动一步，这样，随着不断提交，`master`分支的线也越来越长。

当我们创建新的分支，例如`dev`时，Git新建了一个指针叫`dev`，指向`master`相同的提交，再把`HEAD`指向`dev`，就表示当前分支在`dev`上：
```
$ git checkout -b dev
//相当于
//git branch dev
//git checkout dev

//git branch 查看当前分支
```
![[Pasted image 20241128110506.png|200]]

从现在开始，对工作区的修改和提交就是针对`dev`分支了，比如新提交一次后，`dev`指针往前移动一步，而`master`指针不变：
![[Pasted image 20241128110619.png|200]]

在`dev`上的工作完成了，就可以把`dev`合并到`master`上。Git怎么合并呢？最简单的方法，就是直接把`master`指向`dev`的当前提交，就完成了合并：
```
$ git checkout master //切回master分支
$ git merge dev       //合并dev分支
```
![[Pasted image 20241128110706.png|200]]

合并分支后，甚至可以删除`dev`分支：
```
$ git branch -d dev
```

##### switch
切换分支使用`git checkout <branch>`，而前面讲过的撤销修改则是`git checkout -- <file>`

最新版本的Git提供了新的`git switch`命令来切换分支

创建并切换到新的分支：`git switch -c dev`
直接切换到已有分支：`git switch master`

### 解决冲突
多个分支同时有新的提交，修改合并产生冲突
必须手动解决后再提交

Git用`<<<<<<<`，`>>>>>>>`标记出不同分支的内容

![[Pasted image 20241128112519.png|200]]

用带参数的`git log`也可以看到分支的合并情况
```plain
$ git log --graph --pretty=oneline --abbrev-commit
```

### 分支管理策略
`Fast forward`模式，删除分支后，会丢掉分支信息。

如果要强制禁用`Fast forward`模式，Git就会在merge时生成一个新的commit，这样，从分支历史上就可以看出分支信息。
```plain
$ git merge --no-ff -m "merge with no-ff" dev
```

##### 分支策略
首先，`master`分支应该是非常稳定的，也就是仅用来发布新版本，平时不能在上面干活；
那在哪干活呢？干活都在`dev`分支上，也就是说，`dev`分支是不稳定的，到某个时候，比如1.0版本发布时，再把`dev`分支合并到`master`上，在`master`分支发布1.0版本；
你和你的小伙伴们每个人都在`dev`分支上干活，每个人都有自己的分支，时不时地往`dev`分支上合并就可以了。
![[Pasted image 20241128133428.png|300]]
### Bug分支
软件开发中，bug就像家常便饭一样。有了bug就需要修复，在Git中，由于分支是如此的强大，所以，每个bug都可以通过一个新的临时分支来修复，修复后，合并分支，然后将临时分支删除。

Git还提供了一个`stash`功能，可以把当前**工作现场**“储藏”起来，等以后恢复现场后继续工作（工作暂停，debug启动）
工作现场用`git stash list`命令查看
工作现场恢复：
`git stash apply` （恢复后stash内容不删除， 用`git stash drop`删除）
`git stash pop` （恢复的同时删除内容）


同样的bug，要在`dev`上修复，我们只需要把`4c805e2 fix bug 101`这个提交所做的修改“复制”到`dev`分支。注意：我们只想复制`4c805e2 fix bug 101`这个提交所做的修改，并不是把整个`master`分支merge过来。
为了方便操作，Git专门提供了一个`cherry-pick`命令，让我们能复制一个特定的提交到当前分支。

Git自动给`dev`分支做了一次提交，注意这次提交的commit是`1d4b803`，它并不同于`master`的`4c805e2`，因为这两个commit只是改动相同，但确实是两个不同的commit。用`git cherry-pick`，我们就不需要在`dev`分支上手动再把修bug的过程重复一遍。
```plain
$ git branch
* dev
  master
$ git cherry-pick 4c805e2
[master 1d4b803] fix bug 101
 1 file changed, 1 insertion(+), 1 deletion(-)
```
### Feature分支
添加一个新功能时，你肯定不希望因为一些实验性质的代码，把主分支搞乱了，所以，每添加一个新功能，最好新建一个feature分支，在上面开发，完成后，合并，最后，删除该feature分支。

如果要丢弃一个没有被合并过的分支，可以通过`git branch -D <name>`强行删除。

### 多人协作
当你从远程仓库克隆时，实际上Git自动把本地的`master`分支和远程的`master`分支对应起来了，并且，远程仓库的默认名称是`origin`。

要查看远程库的信息，用`git remote`，`git remote -v`，`git remote -vv`

##### 推送分支
推送分支，就是把该分支上的所有本地提交推送到远程库。推送时，要指定本地分支，这样，Git就会把该分支推送到远程库对应的远程分支上：
```plain
$ git push origin master
```

总之，就是在Git中，分支完全可以在本地自己藏着玩，是否推送，视你的心情而定！

##### 抓取分支※
多人协作时，大家都会往`master`和`dev`分支上推送各自的修改。

当你的小伙伴从远程库clone时，默认情况下，你的小伙伴只能看到本地的`master`分支。

**要在`dev`分支上开发，就必须创建远程`origin`的`dev`分支到本地**，于是他用这个命令创建本地`dev`分支：
```plain
$ git checkout -b dev origin/dev
```


推送失败，因为你的小伙伴的最新提交和你试图推送的提交有冲突，解决办法也很简单，Git已经提示我们，先用`git pull`把最新的提交从`origin/dev`抓下来，然后，在本地合并，解决冲突，再推送。

### Rebase
多人在同一个分支上协作时，很容易出现冲突。即使没有冲突，后push的童鞋不得不先pull，在本地合并，然后才能push成功。

- rebase操作可以把本地未push的分叉提交历史整理成直线；
- rebase的目的是使得我们在查看历史提交的变化时更容易，因为分叉的提交需要三方对比。

# 标签管理
发布一个版本时，我们通常先在版本库中打一个标签（tag），这样，就唯一确定了打标签时刻的版本
tag就是一个让人容易记住的有意义的名字，它跟某个commit绑在一起

### 创建标签
敲命令`git tag <name>`就可以打一个新标签，默认标签是打在最新提交的commit上的。
若之前的commit忘记打标签，也可：`git tag <name> <commit id>`

用命令`git tag`查看标签
用`git show <tagname>`查看标签信息

可以创建带有说明的标签，用`-a`指定标签名，`-m`指定说明文字

### 操作标签
删除标签：`$ git tag -d v0.1`
因为创建的标签都只存储在本地，不会自动推送到远程。所以，打错的标签可以在本地安全删除。

如果要推送某个标签到远程，使用命令`git push origin <tagname>`
或者，一次性推送全部尚未推送到远程的本地标签：`git push origin --tags`

如果标签推送到远程，删除得先本地删除，后从远程删除
远程删除格式：`$ git push origin :refs/tags/v0.9`


# 使用SourceTree
图形化工具

# 常用命令
push到远程分支：`git push origin master:dev`
查看本地分支和远程分支的跟踪关系：`git branch -vv`
从远程分支创建本地分支：`git checkout -b dev origin/dev`
![[git-cheat-sheet.jpg|600]]



# 其他

## Git Flow分支模型
#### 1. `master`（或 `main`）分支
- **功能**：`master` 分支是 Git Flow 模型中的主要分支，代表着**生产环境的稳定代码**。每次发布一个新版本时，都会将代码合并到 `master` 分支，并通常在该分支上打上版本标签。
- **在远程仓库中的作用**：`master` 是远程仓库中用于发布稳定版本的分支，通常是团队所有开发人员的工作目标。这个分支应该始终处于可发布的状态，任何时候都应该是稳定且经过测试的代码。
- **远程仓库**：在远程仓库中，`master` 是一个被广泛使用的主分支。在 GitHub、GitLab 等平台上，`master`（或者 `main`）是默认的分支名称。

#### 2. `develop` 分支
- **功能**：`develop` 是开发分支，用于集成所有的开发特性。它通常是从 `master` 分支派生出来的，并作为集成开发的主分支。在 `develop` 分支上，开发人员进行日常的开发工作。
- **在远程仓库中的作用**：`develop` 是远程仓库中的集成开发分支，团队成员将各自的功能分支合并到这个分支，以便在开发过程中保持一个较为稳定的代码基础。
- **远程仓库**：与 `master` 分支一样，`develop` 通常也会存在于远程仓库中，并且作为日常开发的主要协作分支。

#### 3. `feature/` 分支
- **功能**：`feature/` 分支用于开发新功能。每个新功能都会从 `develop` 分支派生，并在开发完成后将其合并回 `develop`。这些分支通常是短期存在的，在功能开发完成后会删除。
- **在远程仓库中的作用**：`feature/` 分支通常是针对某一具体功能的分支，它可以推送到远程仓库，方便团队成员共享和协作。每个 `feature/` 分支通常对应一个任务或一项功能。
- **远程仓库**：`feature/` 分支会被推送到远程仓库，但它们通常会在功能完成后删除。不同的开发人员可能会同时创建多个 `feature/` 分支。

#### 4. `release/` 分支
- **功能**：当 `develop` 分支上的功能已经基本完成，准备发布一个新版本时，创建一个 `release/` 分支。这是为了准备发布的版本，进行最后的修复、文档更新、版本号更新等。
- **在远程仓库中的作用**：`release/` 分支用于准备发布的版本。当版本准备好时，它会合并回 `master`（表示该版本已准备好发布）和 `develop`（确保最新的开发代码中包含发布的修改）。
- **远程仓库**：`release/` 分支通常会推送到远程仓库，并在发布完成后删除。它是一个临时存在的分支，主要用于版本发布前的最终检查和准备。

#### 5. `hotfix/` 分支
- **功能**：`hotfix/` 分支用于修复生产环境中的紧急问题。通常，当在 `master` 分支上发现紧急问题时，会从 `master` 分支创建一个 `hotfix/` 分支进行修复。修复完成后，`hotfix/` 分支会被合并回 `master` 和 `develop`。
- **在远程仓库中的作用**：`hotfix/` 分支会推送到远程仓库，并用于快速修复生产环境中的问题。`hotfix/` 分支是一个非常临时的分支，修复后通常会删除。
- **远程仓库**：与 `feature/` 和 `release/` 分支类似，`hotfix/` 分支会推送到远程仓库，但通常在问题修复后删除。

#### 6. 分支管理和远程仓库
在 Git Flow 中，所有的这些分支（`master`、`develop`、`feature/`、`release/`、`hotfix/`）都会有远程对应的分支，通常存储在一个远程仓库（如 GitHub 或 GitLab）中。这使得团队成员可以共同协作，并通过 `git push` 和 `git pull` 来同步彼此的更改。

## Pull Request (PR)规范
### 概述
pull request（以下用pr代称） 需要严格遵循以下原则：
- 一个 pr 只围绕一件事
- 避免过大的 pr
#### 一个 pr 只围绕一件事
一个 pr 应该只负责一件事，这遵循设计模式中的**单一职责原则**
如何定义一件事：
- 处理了一个 issue
- 解决了一个bug
- 新增了一个组件或功能
- 重构代码实现了某**一个**目的
> **一个 pr 可以包含多个 commit，但要注意尺度，保证 pr 不要过大**

#### 避免过大的 pr
> 该条规则对于新增组件的 pr 例外

一个 pr 的文件改变最好少于**12个文件**（排除build产生的文件）

### 信息填写
#### Title

##### Pr 仅包含一个 commit
直接使用 Github 默认填写的信息，即 Title 为 commit msg 的 subject 部分，Content 为 commit msg 的 body 部分
##### Pr 包含多个 commit
描述清楚这个 Pr 所做的事情，格式：`[名词]`+`动词`+`名词`+`[形容词]`+`[名词]`
例如：
- 修复 Collapse 组件无法展开的问题
- Collapse 组件添加 top 属性
- 新增 Message 组件
- 删除 Message 组件 color 属性
- 修改 Message 组件 top 属性单位为 rpx

> 注意英文单词左右添加一个空格方便阅读

动词建议从下列选项中选取：
- 新增（组件、属性、API）
- 修改
- 修正
- 删除
#### Content
如果 title 已经描述清楚了此次 pr 的目的，则 Content 可以留空，否则应该对此次 pr 进行详细的描述

### 其他规则
#### 连接 issue
如果这个 pr 解决了某个 issue 提出的 bug 或者 feature，则应在 pr 中将此 issue 关联起来
在 pr 描述中 使用如下关键字可将 issue 关联起来：
- close
- closes
- closed
- fix
- fixes
- fixed
- resolve
- resolves
- resolved

> 关联 issue 的好处：
> - 可以在 issue 界面快速跳转到这个 pr，查看修复的情况
> - 在该 pr 被合并进 master 分支后，对应 issue 会被自动 close。所以连接了 pr 的 issue 不需要手动 close

## 重置仓库
从 Gitee 克隆一个项目进行二次开发时，如果你希望删除该项目的历史提交记录，通常是为了清理不需要的历史或重写项目的历史。以下是如何删除克隆项目中之前的 commit 的方法。注意：修改提交历史会影响到项目的版本控制历史，请谨慎操作，尤其是在团队协作时，避免影响其他开发者。
### 1. **删除所有历史提交（清空历史并重新开始）**
如果你想删除该项目的所有历史提交，并将仓库重置为一个全新的提交记录，可以通过以下步骤进行：
#### 1.1 **重置 Git 仓库的历史**

1. **删除 `.git` 目录**：首先，你需要删除原有的 `.git` 目录。这会清空 Git 的历史记录，变成一个没有版本控制的项目。
    `rm -rf .git`
    这样，当前项目就不再是一个 Git 仓库。
2. **重新初始化 Git 仓库**：
    在项目目录中重新初始化一个 Git 仓库：
    `git init`
3. **添加所有文件并提交**：
    现在，你的项目已经没有历史提交了。你可以将所有文件添加到暂存区，并进行第一次提交：
    `git add . git commit -m "Initial commit after history cleanup"`
4. **关联远程仓库并推送**：
    将本地仓库推送到 Gitee 上的远程仓库：
    `git remote add origin <repository_url> git push -u origin master --force`
    这时，远程仓库会重写为你的新提交历史。
#### 1.2 **注意：** 强制推送会覆盖远程仓库的历史，因此必须小心。如果其他团队成员已经基于该仓库进行开发，强制推送可能导致他们的本地仓库出现问题。

### 2. **删除部分历史提交（使用 `git rebase -i`）**
如果你只想删除某些特定的历史提交，而不是完全清空历史，可以使用交互式 rebase (`git rebase -i`) 来删除某些提交。
#### 2.1 **使用 `git rebase -i` 删除提交**
1. 使用 `git log` 查看提交历史，找到你想删除的提交的哈希值。
    `git log --oneline`
2. 假设你要删除最近的 5 次提交，执行交互式 rebase：
    `git rebase -i HEAD~5`
3. 这会打开一个编辑器，显示最近的 5 次提交
4. 将你想删除的提交前面的 `pick` 改为 `drop`
5. 保存并退出编辑器，Git 会重新应用剩余的提交
6. 如果遇到冲突，Git 会暂停并提示你解决冲突。解决冲突后，可以使用以下命令继续
    `git rebase --continue`

#### 2.2 **推送更新到远程仓库**
完成本地修改后，使用强制推送将修改后的历史推送到 Gitee 上：
`git push origin <branch_name> --force`

### 3. **删除某个特定的提交（`git rebase` 或 `git filter-branch`）**
如果你只想删除某个特定的提交，而不是最近的提交，可以使用 `git rebase -i` 来选择性删除某个提交。或者，对于更复杂的场景，使用 `git filter-branch` 进行历史修改。
#### 3.1 **删除某个特定的提交（使用 `git rebase -i`）**
1. 使用 `git log` 找到你想删除的提交的哈希值。
2. 执行交互式 rebase：
    `git rebase -i <commit_hash>^`
    这将打开编辑器，允许你选择删除或修改该提交。
3. 在编辑器中，找到目标提交并将 `pick` 改为 `drop`，然后保存并退出。

#### 3.2 **使用 `git filter-branch` 删除某个提交或敏感信息**
`git filter-branch` 是一个更高级的工具，可以用于删除历史中的某些特定文件或提交。例如，删除某个特定的文件：
`git filter-branch --tree-filter 'rm -f <file_path>' HEAD`
这会删除项目历史中所有提交中的 `<file_path>` 文件。


## 本地分支与远程分支关联
### 1. **拉取远程分支的信息**
首先，使用 `git fetch` 获取远程仓库中的最新分支信息。如果远程仓库中已经存在 `dev` 分支，`git fetch` 会更新本地的远程分支列表。

### 2. **检查远程分支**
确保远程仓库确实有 `dev` 分支。使用以下命令查看所有远程分支：`git branch -r`

如果看到 `origin/dev` 分支，说明远程仓库中确实有该分支。如果没有，需要创建远程的 `dev` 分支。

### 3. **关联本地分支到远程 dev 分支**
如果远程仓库中的 `dev` 分支确实存在，你可以尝试再次关联：`git branch --set-upstream-to=origin/dev dev`

### 4. **如果远程没有 dev 分支，创建远程 dev 分支并推送**
如果远程仓库没有 `dev` 分支，且你希望将本地的 `dev` 分支推送到远程，并且让它关联远程的 `dev` 分支，可以使用：`git push -u origin dev`
这会将本地的 `dev` 分支推送到远程，并设置关联。

### 5. **验证关联是否成功**
可以使用以下命令确认本地分支是否成功关联到远程分支：
`git branch -vv`


