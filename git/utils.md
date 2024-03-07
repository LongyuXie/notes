## Git的常用命令

- 新建分支: `git branch <new_branch_name>`
- 从提交历史版本中创建新分支: `git checkout -b branch_name version_id`
    - branch_name 是新的分支的名字
    - version_id 是提交的版本号, 例如: b9e998f2fcb9042aa5f88986b6ccf90327496435.
- 撤销最后一次提交, 并且保留修改后的文件: `git reset --soft HEAD^`
- 撤销最后一次提交, 不保留修改后的文件: `git reset HEAD^`
- 撤销提交后, 恢复提交: `git reset --hard <commit_hash_or_tag>`
