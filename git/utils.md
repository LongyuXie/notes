## 常用命令

- 新建分支: `git branch <new_branch_name>`
- 基于某个版本提交新建分支: `git checkout -b <new_branch_name> <commit_hash_or_tag>`
- 撤销最后一次提交, 并且保留修改后的文件: `git reset --soft HEAD^`
- 撤销最后一次提交, 不保留修改后的文件: `git reset HEAD^`
- 撤销提交后, 恢复提交: `git reset --hard <commit_hash_or_tag>`
