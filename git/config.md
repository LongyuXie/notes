## Git的基本配置

- 配置文件位置

  - 全局配置文件：`~/.gitconfig`
  - 仓库配置文件：`.git/config`

- 查看配置文件：`git config --<score> --list`，scope包括三个字段：system，global，local，一般只需要修改全局配置文件即可

- 配置用户名，密码和邮箱：

  - `git config --global user.name "xielongyu"`
  - `git config --global user.email "xxx@xxx"`
  - `git config --global user.password xxxxxx`
  - 实际使用中需要设置用户名和邮箱才可以再本地进行commit操作

  