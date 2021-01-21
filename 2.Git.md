# Git

git add . //git会自动查找变更过的文件然后提交到暂存区

git commit -m '描述'  //提交到本地仓库

git push -u origin master //提交到远程仓库注意配置orign

git pull origin master //如果无法提交先拉下来再提交

git remote add origin1 码云ssh//可以利用其同步GitHub然后pull包防止过慢 push 不影响

git push -u origin master //把包推到远程仓库的master节点，远程仓库一一匹配 其实就是ssh对应的仓库名称，我们起的别名叫做orign,orign1是码云上的仓库，不起同样的名字防止混淆

git 密钥问题 

# 创建删除远程分支（用于远程仓库创建错了的问题）

先输入 git remote rm origin

再输入 git remote add origin  **

# 用于删除远程仓库 节点下某个文件夹

git rm -r --cached 文件名  #--cached不会把本地的.idea删除
git commit -m 'delete 文件名 dir'
git push -u origin master 



