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

- 推送改动
> git push origin &ltbranch_name&gt

- 连接远程服务器
> git remote add origin &ltserver&gt //注意：origin是&ltserver&gt的别名

- 更新本地仓库至最新
> git pull //会尝试自动合并

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

- 打标签
> git tag 1.0.0 &ltcommit_id&gt

- 查看仓库记录
> git log
> git log --help //打开网页查看help

- 替换工作目录的改动（暂存区不会受影响），用head替换
> git checkout -- &ltfilename&gt
> git checkout .
> git checkout &ltbranch_name&gt

- 图形化工具
> gitk

- 

