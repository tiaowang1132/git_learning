# git命令学习

## 本地命令
git add 从工作区添加到缓存区（filename）
git commit 缓存区到分支里面（-m "XXXX"）
图略<br>
git status 查看更改状态
git diff 查看具体改了啥
git log 查看操作记录
git reflog 查看历史记录（如果有操作被覆盖了可查commit id）
git reset --hard [commitid]（id开始几个字母就行了会自动匹配）用于回到commitid时的状态
图略<br>

git reset HEAD filename 将缓存区（还未提交到分支）的内容清空，并退回到工作区
图略<br>
git checkout -- filename 将工作区回退到最后一次add（缓存区）或者commit（分支）的状态（其实该命令作用就是同步分支（缓存区）里面的代码到工作区）
图略<br>
`__删除文件之后可以通过git add filename或git rm filename；然后commit来同步分支中的代码__`

## 远程控制
git clone gitaddress 克隆远程代码到本地
git remote add origin git@github.com:tiaowang1132/learngit.git 将本地仓库和远程仓库关联
git push -u origin master 将本地仓库代码推到远程(第一次推送所有内容)
git push origin master 平时commit之后同步给远程的命令
`在这里有个问题，就是操作者的信息会提交到github里面的记录里，为了不暴露公司的邮箱（比如公司邮箱设置的时global），在__当前仓库__使用git config user.name "XXX" 和git config user.email "xxx@xxx.com"`

## 分支管理
### 创建与合并
git checkout -b dev 创建dev分支并切到dev分支（=git branch dev单纯创建&&git checkout dev切换分支）
git branch 查看当前分支
图略<br>
git merge dev 将dev分支代码同步到当前分支
git branch -d dev 删除分支
git merge --no-ff -m "XXXX" dev 不使用fastforward模式（即普通模式）
### 解决冲突
当不同分支同时修改了某一个文件的同一行时，合并（merge）的时候会有冲突
图略<br>
这个时候手动编辑当前当前版本（一般是master）的相应文档，重新add&commit
解决之后可以通过git log --graph查看合并过程
图略<br>

### stash的用法
设A为游戏软件 1、master 上面发布的是A的1.0版本 2、dev 上开发的是A的2.0版本 3、这时，用户反映 1.0版本存在漏洞，有人利用这个漏洞开外挂 4、需要从dev切换到master去填这个漏洞，正常必须先提交dev目前的工作，才能切换。 5、而dev的工作还未完成，不想提交，所以先把dev的工作stash一下。然后切换到master 6、在master建立分支issue101并切换. 7、在issue101上修复漏洞。 8、修复后，在master上合并issue101 9、切回dev，恢复原本工作（ git stash apply ，git stash drop）/（git stash pop），继续工作。
git cherry-pick commitid（issue101中fixbug的id） 同步（如上场景中，将master的更改同步到dev）
### 其他（比如 git rebase）
目前没怎么使用


