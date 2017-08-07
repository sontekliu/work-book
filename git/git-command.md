### Git常用命令讲解  

#### Git 配置

|序号  | 命令                                          | 说明
|:----:|-----------------------------------------------|-------------------
| 01   | `git config --global user.name "xxxxx"`       | 配置用户名
| 02   | `git config --global user.email "xx@xx.com"`  | 配置邮件
| 03   | `git config --global color.ui true`           | 配置自动着色
| 04   | `git config --global color.status auto`       | 配置自动着色
| 05   | `git config --global color.diff auto`         | 配置自动着色 
| 06   | `git config --global color.branch auto`       | 配置自动着色 
| 07   | `git config --global color.interactive auto`  | 配置自动着色
| 08   | `git config --global core.editor vim`         | 配置Git编辑工具
| 09   | `git config --global merge.tool vimdiff`      | 配置Git合并工具
| 10   | `git config --global alias.co checkout`       | 配置别名
| 11   | `git config --global alias.ci commit`         | 配置别名
| 12   | `git config --global alias.br branch`         | 配置别名
| 13   | `git config --global alias.st status`         | 配置别名

#### Git 常用 

|序号  | 命令                                                | 说明
|:----:|-----------------------------------------------------|-------------------------------------------------------------
| 01   | `git init`                                          | 初始化仓库
| 02   | `git status`                                        | 查看工作区状态
| 03   | `git add <file>...`                                 | 向暂存区域添加文件
| 04   | `git commit -m "备注内容"`                          | 向数据仓库提交修改内容
| 05   | `git commit -am "备注内容"`                         | add 和 commit 合并为一步
| 06   | `git push origin master`                            | 将当前分支提交到远程分支
| 07   | `git push -u origin master`                         | 第一次推送master分支的所有内容
| 08   | `git clone git@server-name:path/repo-name.git`      | 从远程仓库克隆
| 09   | `git rm <file>`                                     | 删除文件
| 10   | `git mv <file> <file2>`                             | 文件重命名
| 11   | `git diff`                                          | 查看未添加到暂存的变更
| 12   | `git diff --cached`                                 | 查看已添加暂存但还未commit的变更
| 13   | `git diff HEAD^`                                    | 比较与上一版本的差异
| 14   | `git diff origin/master master`                     | 比较本地已提交，而远程没有的东西
| 15   | `git reset --hard HEAD`                             | 将当前版本重置为 HEAD，常用于 merge 失败回退
| 16   | `git reset --hard HEAD^`                            | 回到上一版本
| 17   | `git reset --hard HEAD^^`                           | 回到上上一个版本
| 18   | `git reset --hard HEAD~100`                         | 回到上100个版本
| 19   | `git reset --hard <id>`                             | 回到某个提交的版本，例如:`git reset --hard ea3457`
| 20   | `git checkout -- <file>`                            | 撤销对file修改。即，返回文件最后一次git commit或者git add时的状态，如果文件进入暂存区域此命令无法撤销。
| 21   | `git reset HEAD <file>`                             | 将文件从暂存区域撤回，即:unstage
| 22   | `git reflog`                                        | 记录每一次执行的命令，查看命令历史
| 23   | `git stash`                                         | 把当前工作的现场"储藏"起来
| 24   | `git stash list`                                    | 查看"储藏"列表
| 25   | `git stash apply`                                   | 恢复"储藏"现场，但是stash内容并不删除，即，git stash list 还可以查看
| 26   | `git stash drop`                                    | 删除stash内容，即，git stash list查看不到
| 27   | `git stash pop`                                     | 恢复"储藏"现场，并删除stash内容

#### Git 日志

|序号  | 命令                                               | 说明
|:----:|----------------------------------------------------|------------------------
| 01   | `git log`                                          | 查看提交日志
| 02   | `git log -n`                                       | 显示N行日志
| 03   | `git log -p -m`                                    | 显示提交日志以及相关变动文件
| 04   | `git log --stat`                                   | 显示提交日志以及相关变动文件
| 05   | `git log --pretty=oneline`                         | 查看提交日志单行显示
| 06   | `git log --graph --pretty=oneline --abbrev-commit` | 查看分支合并情况，`--abbrev-commit`简化ID的显示
| 07   | `git log v2.0`                                     | 显示 v2.0 的日志
| 08   | `git show dfb02`                                   | 查看某个提交的详细内容
| 09   | `git show HEAD`                                    | 显示 HEAD 提交的日志
| 10   | `git show HEAD^`                                   | 显示 HEAD 上一版本提交的日志
| 11   | `git show HEAD^N`                                  | 显示 HEAD 上N版本提交的日志，N 为数字
| 12   | `git show v2.0`                                    | 显示 v2.0 的日志以及详细内容

#### Git 分支

|序号  | 命令                                  | 说明
|:----:|---------------------------------------|----------------------------
| 01   | `git branch`                          | 查看拥有分支
| 02   | `git branch -a`                       | 查看所有
| 03   | `git branch -r`                       | 查看所有原创
| 04   | `git branch --merged`                 | 查看所有已合并到当前分支的分支
| 05   | `git branch --no-merged`              | 查看所有未合并到当前分支的分支
| 06   | `git branch -m master master1`        | 本地分支改名
| 07   | `git branch name`                     | 创建分支
| 08   | `git branch -d name`                  | 删除分支
| 09   | `git branch -D name`                  | 强行删除分支
| 10   | `git checkout name`                   | 切换到某分支或 Tag
| 11   | `git checkout -b name`                | 创建+切换分支
| 12   | `git checkout -b dev origin/dev`      | 在本地创建和远程分支对应的分支
| 13   | `git merge name`                      | 合并name分支到当前分支
| 14   | `git push origin v1.1`                | 推送某个标签到远程仓库
| 15   | `git push origin dev`                 | 推送dev分支到远程仓库
| 16   | `git push origin --tags`              | 推送所有尚未推送到远程的本地标签
| 17   | `git push origin :refs/tags/<tagname>`| 删除远程仓库标签
| 18   | `git push origin :remote-branch`      | 删除远程分支
| 19   | `git fetch`                           | 获取所有远程分支，但是不合并到本地分支
| 20   | `git pull origin master`              | 获取所有远程分支，并合并到当前分支

#### Git Tag

|序号  | 命令                                 | 说明
|:----:|--------------------------------------|--------------------------------
| 01   | `git tag`                            | 查看所有标签
| 02   | `git tag <name>`                     | 打标签
| 03   | `git tag <name> commid`              | 在某次提交上打标签
| 04   | `git tag -a <name> -m "xx"`          | 添加 name 的tag
| 05   | `git tag -a <name> -m "xx" commid`   | 在某次提交上打标签并添加备注
| 06   | `git show <name>`                    | 查看标签信息
| 07   | `git tag -d v1.1`                    | 删除标签

#### Git 远程

|序号  | 命令                                            | 说明
|:----:|-------------------------------------------------|--------------------------------
| 01   | `git remote`                                    | 查看远程库的信息
| 02   | `git remote -v`                                 | 查看远程库的详细信息
| 03   | `git clone git@server-name:path/repo-name.git`  | 从远程仓库克隆
| 04   | `git push origin v1.1`                          | 推送某个标签到远程仓库
| 05   | `git push origin dev`                           | 推送dev分支到远程仓库
| 06   | `git push origin --tags`                        | 推送所有尚未推送到远程的本地标签
| 07   | `git push origin :refs/tags/<tagname>`          | 删除远程仓库标签
| 08   | `git push origin :remote-branch`                | 删除远程分支
| 09   | `git fetch`                                     | 获取所有远程分支，但是不合并到本地分支
| 10   | `git pull origin master`                        | 获取所有远程分支，并合并到当前分支



