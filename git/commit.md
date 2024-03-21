
## Git commit 规范

基本格式: `<type>(<scope>)`: <subject>

- type(必须)
    - feat: 新功能, feature
    - fix/to: 修复bug
    - docs: 文档修改
    - style: 修改格式, 不影响代码的变动
    - refactor: 重构, 不改变原有功能, 也没有修复bug
    - perf: 优化相关, 例如提升性能, 体验
    - test: 增加测试
    - chore: 构建过程或者辅助工具变动
    - revert: 回滚到上一个版本
    - merge: 代码合并
    - sync: 同步主线或者分支的bug
- scope(可选)
    - scope说明commit影响的范围, 例如数据层, 控制层, 视图层等
- subject(必须)
    - 说明commit的目的, 简短描述
