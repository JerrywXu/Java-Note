# Git

git add . //git会自动查找变更过的文件然后提交到暂存区

git commit -m '描述'  //提交到本地仓库

git push -u origin master //提交到远程仓库注意配置orign

git push -u origin master -f  //强制push本地仓库到远程 (这种情况不会进行merge, 强制push后远程文件可能会丢失 不建议使用此方法)

git pull origin master //如果无法提交先拉下来再提交

git remote add origin1 码云ssh//可以利用其同步GitHub然后pull包防止过慢 push 不影响

git push -u origin master //把包推到远程仓库的master节点，远程仓库一一匹配 其实就是ssh对应的仓库名称，我们起的别名叫做orign,orign1是码云上的仓库，不起同样的名字防止混淆

git rebase --abort//会放弃合并，回到rebase操作之前的状态，之前的提交的不会丢弃

git merge --no-ff -m "merge with no-ff" dev //合并分支时，加上`--no-ff`参数就可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并，而`fast forward`合并就看不出来曾经做过合并。



git 密钥问题 ssh

# 创建删除远程分支（用于远程仓库创建错了的问题）

先输入 git remote rm origin //删除远程仓库

再输入 git remote add origin  ** //添加远程仓库

# 用于删除远程仓库 节点下某个文件夹

git rm -r --cached 文件名  #--cached不会把本地的.idea删除
git commit -m 'delete 文件名 dir'
git push -u origin master 

# merge 、rebase、fetch的区别

Git鼓励大量使用分支：

查看分支：git branch

创建分支：git branch <name>

切换分支：git checkout <name>或者git switch <name>

创建+切换分支：git checkout -b <name>或者git switch -c <name>

合并某分支到当前分支：git merge <name>

删除分支：git branch -d <name>

![image-20210121212220386](C:\Users\徐纪伟\AppData\Roaming\Typora\typora-user-images\image-20210121212220386.png)



当本地master比远程慢的时候，提交本地master上的feature可能会产生冲突，需要把本地master pull下来冲突的地方改为和feature一样再把feature提交上去即可，然后删除feature分支

![image-20210121212712643](C:\Users\徐纪伟\AppData\Roaming\Typora\typora-user-images\image-20210121212712643.png)

merge: 合并分支，建议在分支上工作然后再merge到主分支上再删除工作的分支，这样会有进度 

rebase：把分叉的提交历史“整理”成一条直线，看上去更直观。缺点是本地的分叉提交已经被修改过了。rebase的目的是使得我们在查看历史提交的变化时更容易，因为分叉的提交需要三方对比。

fetch：使用git fetch更新代码，本地的库中master的commitID不变，还是等于1。但是与git上面关联的那个orign/master的commit ID变成了2。这时候我们本地相当于存储了两个代码的版本号，我们还要通过merge去合并这两个不同的代码版本，如果这两个版本都修改了同一处的代码，这时候merge就会出现冲突，然后我们解决冲突之后就生成了一个新的代码版本。



