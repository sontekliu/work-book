## Git常用命令讲解  

1. `git init`	初始化仓库           
2. `git add \<file\>...`  向暂存区域添加文件           
3. `git commit -m "备注内容"`	向数据仓库提交修改内容     
4. `git status`	查看工作区状态    
5. `git diff`   查看修改内容       
6. `git log`	查看提交日志      
7. `git log --pretty=oneline`	查看提交日志单行显示      
8. `git reset --hard HEAD^`		回到上一版本        
9. `git reset --hard HEAD^^`	回到上上一个版本
10. `git reset --hard HEAD~100` 回到上100个版本
11. `git reset --hard \<id\>`   回到某个提交的版本，例如:`git reset --hard ea3457`      
12. `git reflog`	记录每一次执行的命令，查看命令历史               
13. `git checkout -- \<file\>` 撤销对file修改。即，返回文件最后一次git commit或者git add时的状态，
     如果文件进入暂存区域此命令无法撤销。
14. `git reset HEAD \<file\>`   将文件从暂存区域撤回，即:unstage    
15. `git rm \<file\>`   删除文件      
16. `git mv \<file\> \<file2\>`   文件重命名         

