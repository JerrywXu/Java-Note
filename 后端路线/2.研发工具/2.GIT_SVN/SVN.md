[![logo](img/favicon.png)](https://svnbucket.com/posts/)

# svn常用命令

svn的命令通常都很少用，在windows上，我们通常都是使用图形化的操作界面，例如 TortoiseSVN 提供了很好的图形化操作界面，上手简单方便。
但是有时候我们需要在服务器这类没有图形化操作界面的机器上使用svn，这时候我们就需要用到svn的命令来操作了。
本篇给大家讲解一些svn的常用命令，日常使用学会这些就足够了。

https://svnbucket.com（SVN）

```
# 代码检出，checkout也可以简写为co，这个命令会把服务器上的代码同步到我们电脑上
svn checkout svn://svnbucket.com/xxx/xxx
# 更新代码，执行此命令后会把其他人提交的代码全部更新到我们自己电脑上，update也可以简写为up
svn update
# 提交代码，commit可以简写为ci，-m参数后面跟的是本次提交的描述内容
svn commit -m "提交描述"
# 添加新文件到版本库，只是标记了添加到版本库，我们还需要执行提交命令这个文件才会提交到服务器上
svn add filename
# 添加当前目录下所有php文件
svn add *.php
# 递归添加当前目录下的所有新文件
svn add . --no-ignore --force
# 查看指定文件的所有log
svn log test.php
# 查看指定版本号的log
svn svn log -r 100
# 撤销本地文件的修改（还没提交的）
svn revert test.php
svn revert -r 目录名
# 撤销目录下所有本地修改
svn revert --recursive 目录名
# 查看当前工作区的所有改动
svn diff
# 查看当前工作区test.php文件与最新版本的差异
svn diff test.php  
# 指定版本号比较差异
svn diff -r 200:201 test.php  
# 查看当前工作区和版本301中bin目录的差异
svn diff -r 301 bin
# 查看当前工作区的状态
svn status
# 查看svn信息
svn info
# 查看文件列表，可以指定-r查看，查看指定版本号的文件列表
svn ls 
svn ls -r 100
# 显示文件的每一行最后是谁修改的（出了BUG，经常用来查这段代码是谁改的）
svn blame filename.php
# 查看指定版本的文件内容，不加版本号就是查看最新版本的
svn cat test.py -r 2
# 清理，这个命令我们经常在svn出现报错时可以执行一下，这样就会清理掉本地的一些缓存
svn cleanup
# 若想创建了一个文件夹，并且把它加入版本控制，但忽略文件夹中的所有文件的内容
svn mkdir spool 
svn propset svn:ignore '*' spool 
svn ci -m 'Adding "spool" and ignoring its contents.'
# 若想创建一个文件夹，但不加入版本控制，即忽略这个文件夹
svn mkdir spool 
svn propset svn:ignore 'spool' . 
svn ci -m 'Ignoring a directory called "spool".'
# 切换当前项目到指定分支。服务器上更新新版本我们经常就用这个命令来把当前代码切换到新的分支
svn switch svn://svnbucket.com/test/branches/online1.0
# 重定向仓库地址到新地址。如果你的svn地址变了，不需要重新checkout代码，只需要这样重定向一下就可以了。
svn switch --relocate 原svn地址 新svn地址
# 创建分支，从主干创建一个分支保存到branches/online1.0
svn cp -m "描述内容" http://svnbucket.com/repos/trunk http://svnbucket.com/repos/branches/online1.0
# 合并主干上的最新代码到分支上
cd branches/online1.0
svn merge http://svnbucket.com/repos/trunk 
# 分支合并到主干
svn merge --reintegrate http://svnbucket.com/repos/branches/online1.0
# 删除分支
svn rm http://svnbucket.com/repos/branches/online1.0
# 查看SVN帮助
svn help
# 查看指定命令的帮助信息
svn help commit
```

