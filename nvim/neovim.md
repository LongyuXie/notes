## nvim.api


- 创建缓冲区: `nvim_create_buf({listed}, {scratch})`
    - parameters:
        - {listed}: bool, 是否出现在 buffer 列表中, 可以使用 bnext/bprev 访问.
        - {scrathc}: bool, 是否是临时缓冲区.
    - return:
        - buffer handle, or 0 on error
    - example: `nvim_create_buf(false, true)`

- 新建窗口: `nvim_open_win({buffer}, {enter}, {*config})`
    - parameters:
        - {buffer}: buffer handle, 0 for current buffer.
        - {enter}: bool, 打开并进入该窗口.
        - {config}: table, 窗口配置选项.
    - return:
        - {window}: window handle, 0 on error
    - example: `nvim_open_win(0, true, {relative='cursor', row=4, col=3, width=12, height=3})`

- 隐藏窗口: `nvim_win_hide({window})`. 缓冲区被隐藏, 而不会关闭.
- 关闭窗口: `nvim_win_close({window}, {force})`. 关闭窗口与缓冲区.
- 设置窗口中的 buffer: `nvim_win_set_buf({window}, {buffer})`


- 设置文本行: `nvim_buf_set_lines({buffer}, {start}, {end}, {strict_indexing}, {replacement})`
    - parameters:
        - {buffer}: buffer handle.
        - {start}: number, 左闭右开区间, 下标从0开始, 可以使用负数下标.
        - {end}: number.
        - {strict\_indexing}: bool, 严格模式, 如果为 true, 那么非法下标会报错否则会选择最近的合法下标.
        - {replacement}: bool, 文本行

- 配置 window: `nvim_win_set_option({window}, {name}, {value})`
- 配置 buffer: `nvim_buf_set_option({buffer}, {name}, {value})`
- 创建用户命令: `nvim_create_user_command({name}, {command}, {*opts})`
    - parameters:
        - {name}: string.
        - {command}: string or function. 如果传入一个函数, 那么会有一个[默认参数](https://neovim.io/doc/user/api.html#nvim_buf_create_user_command())
        - {*opts}: table, 命令配置选项

