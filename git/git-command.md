## Git常用命令讲解  
序号   | 命令														 | 说明
-------|------------------------------------------------------------|-------------------------------------------------------------
1.     | `git init`	                                             | 初始化仓库
2.	   | `git add <file>...`                                        | 向暂存区域添加文件
3. 	   | `git commit -m "备注内容"`                                 | 向数据仓库提交修改内容
4. 	   | `git status`	                                             | 查看工作区状态
5. 	   | `git diff`                                                 | 查看修改内容
6. 	   | `git log`	                                                 | 查看提交日志
7. 	   | `git log --pretty=oneline`                                 | 查看提交日志单行显示
8. 	   | `git reset --hard HEAD^`	                                 | 回到上一版本
9. 	   | `git reset --hard HEAD^^`	                                 | 回到上上一个版本
10.	   | `git reset --hard HEAD~100`                                | 回到上100个版本
11.	   | `git reset --hard <id>`                                    | 回到某个提交的版本，例如:`git reset --hard ea3457`
12.	   | `git reflog`                                               | 记录每一次执行的命令，查看命令历史 
13.	   | `git checkout -- <file>`                                   | 撤销对file修改。即，返回文件最后一次git commit或者git add时的状态，如果文件进入暂存区域此命令无法撤销。
14.    | `git reset HEAD <file>`                                    | 将文件从暂存区域撤回，即:unstage 
15.    | `git rm <file>`                                            | 删除文件
16.    | `git mv <file> <file2>`                                    | 文件重命名
17.    | `git remote add origin git@server-name:path/repo-name.git` | 关联远程仓库	
18.    | `git push -u origin master`		                         | 第一次推送master分支的所有内容       
19.    | `git push origin master`		                             | 除第一次外推送最新修改
20.    | `git clone git@server-name:path/repo-name.git`	         | 从远程仓库克隆
21.    | `git branch`	                                             | 查看拥有分支
22.    | `git branch name`	                                         | 创建分支
23.    | `git branch -d name`	                                     | 删除分支
24.    | `git branch -D name`	                                     | 强行删除分支
25.	   | `git checkout name`                                        | 切换到某分支
26.	   | `git checkout -b name`                                     | 创建+切换分支
27.	   | `git merge name`	                                         | 合并name分支到当前分支
28.	   | `git log --graph --pretty=oneline --abbrev-commit`         | 查看分支合并情况，`--abbrev-commit`简化ID的显示   
29.	   | `git stash`	                                             | 把当前工作的现场"储藏"起来     
30.	   | `git stash list`	                                         | 查看"储藏"列表
31.	   | `git stash apply`                                          | 恢复"储藏"现场，但是stash内容并不删除，即，git stash list 还可以查看    
32.	   | `git stash drop`	                                         | 删除stash内容，即，git stash list查看不到     
33.	   | `git stash pop`	                                         | 恢复"储藏"现场，并删除stash内容
34.	   | `git remote`	                                             | 查看远程库的信息
34.	   | `git remote -v`	                                         | 查看远程库的详细信息
34.	   | `git push origin dev`	                                     | 推送dev分支到远程仓库
35.	   | `git checkout -b dev origin/dev`                           | 在本地创建和远程分支对应的分支     	
36.	   | `git pull`	                                             | 从远程仓库拉取最新修改，并在本地合并
37.	   | `git branch --set-upstream branch-name origin/branch-name` | 建立本地分支和远程分支的关联          
38.	   | `git tag`                                                  | 查看所有标签
39.	   | `git tag <name>`                                           | 打标签
40.	   | `git tag <tagname> commit_id`                              | 在某次提交上打标签 
41.	   | `git tag -a <tagname> -m "备注" commit_id`                 | 在某次提交上打标签并添加备注  
42.	   | `git show <tagname>`                                       | 查看标签信息
43.	   | `git tag -d v1.1`                                          | 删除标签
44.	   | `git push origin v1.1`                                     | 推送某个标签到远程仓库
45.	   | `git push origin --tags`                                   | 推送所有尚未推送到远程的本地标签      
46.	   | `git push origin :refs/tags/<tagname>`                     | 删除远程仓库标签
47.	   | `git push origin :remote-branch`                           | 删除远程分支
48.	   | `git config --global alias.co checkout`                    | 配置别名
49.	   | `git config --global alias.ci commit`                      | 配置别名
50.	   | `git config --global alias.br branch`                      | 配置别名
51.	   | `git config --global alias.st status`                      | 配置别名


