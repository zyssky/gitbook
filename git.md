# Git 
作为我日常快速查询git命令的reference

### 原理理解
3个状态：working index（stage）暂存区 head<br/>
分别对应：改了无命令执行后，改了执行add命令后，改了执行add又执行commit后<br/><br/>

### 命令查询

- 初始化
> git init

- 查看分支
> git branch

- 创建分支
> git branch &ltnew_branch_name&gt
> git checkout -b &ltnew_branch_name&gt

- 切换分支
> git checkout &ltbranch_name&gt

- 删除分支
> git branch -d &ltbranch_name&gt

- 检出仓库
> git clone /path/to/repository
> git clone username@host:/path/to/repository //用ssh
> git clone https:/path/to/repository.git //用https

- 添加到暂存区（可以先add再确认是commit到哪个branch）
> git add &ltfilename&gt
> git add *

- 查看仓库状态
> git status



- 提交到head
> git commit -m "代码提交信息"
> git commit --amend [--no-edit] //修复上一次提交(可以选择不修改提交信息)

- 推送改动
> git push &ltremote&gt &ltbranch&gt
> git push origin &ltbranch_name&gt

- 连接远程服务器
> git remote add origin &ltserver&gt //注意：origin是&ltserver&gt的别名

- 更新本地仓库至最新
> git pull //会尝试自动合并
> git pull --rebase //用rebase而不是merge来获取新的改动

- 获取远程分支
> git fetch &ltremote&gt



- 合并其他分支到当前分支
> git merge &ltother_branch&gt

- 查看差异
> git diff //查看工作目录（new）与暂存区（old）的差异
>
> //查看工作目录（new）与传入目标（old）的差异
> git diff &ltcommit_id/branch&gt 
>
> //查看source（old）与target（new）的差异
> git diff &ltsource_branch&gt &lttarget_branch&gt

> //查看暂存区和上次commit的区别
> git diff --cached

- 打标签
> git tag 1.0.0 &ltcommit_id&gt

- 查看仓库记录
> git log
> git log --help //打开网页查看help
> git log --pretty=oneline --graph //以树状图查看log

- 替换工作目录的改动（暂存区不会受影响），用head替换
> git checkout -- &ltfilename&gt
> git checkout .
> git checkout &ltbranch_name&gt

- 图形化工具
> gitk

- 回滚错误提交
> git revert &ltcommit_id&gt //保留上次提交，copy上上次提交覆盖

- 撤销
> git reset &ltfile&gt //取消缓存，不改变工作目录
> git reset //取消缓存，不改变工作目录
> git reset --hard //取消缓存和工作目录
>
> //回到那个commit，前面的提交记录都去掉，但工作目录不变
> git reset &ltcommit_id&gt 
> git reset --hard &ltcommit_id&gt //同时去掉工作目录

- 去除为跟踪的文件
> git clean -n //演戏，查看那些文件会被去除
> git clean -f //真的执行去除未跟踪文件，不可撤销!

- 变基(rebase)，保持线性提交历史
> 例子：
> //在new_feature分支，rebase到master，然后进行快速向前合并
> git checkout new_feature
> git rebase master
> git checkout master
> git merge new-feature



