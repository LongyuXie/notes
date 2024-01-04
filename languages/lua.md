## 冒号与点号

lua 中冒号和点号都可以用来定义函数和调用函数, 简单来说冒号是点号的一种语法糖.

- 函数定义, 以下两种函数定义等价:
  - 冒号定义: `function obj:func(args)`
  - 点号定义: `function obj.func(self, args)`
  - 使用冒号定义的函数将会自动传入一个 `self` 作为第一个参数, 在函数中可以使用 `self` 访问 obj.
  - 点号定义的函数需要手动传入 `self` 作为第一个参数.

- 函数调用, 与函数定义类似使用冒号调用函数时会自动传入 `obj` 作为 `self`: `obj:func(args)` 等价于 `obj.func(obj, args)`


** 总结 **

1. 冒号和点号都可以应用于函数定义和调用两种场合, 冒号是点号的语法糖.
2. 在函数定义时冒号相比于点号会自动传入 `self` 作为第一个参数, 而点号需要手动声明.
3. 在函数调用时冒号相比于点号会自动传入 `self` 作为第一个参数, 而点号需要手动传入.
4. 当对象需要访问自身的成员变量时, 使用冒号定义, 否则使用点号定义.

** 注意 **

冒号不可以使用的情况: `obj:func = function() end`, 这种情况下会报错;
而 `obj.func = function() end` 可以, 因为点号除了定义函数和调用函数之外还可以用来访问字段, 而冒号不行,
点号定义的 `func` 实际上是显式为字段 `func` 赋值一个函数引用.

```lua
Test = {}

Test.test01 = function()
    print(self)
    print("test01")
end

Test.test02 = function(self)
    print(self)
    print("test02")
end

Test.test03 = function(args, ...)
    print(args)
    print(...)
    print("test03")
end


Test.test01() -- nil, test01
Test:test01() -- nil, test01
print("")

Test.test02() -- nil, test02
Test:test02() -- table: 0x, test02
print("")

Test.test03("args") -- args, '', test03
Test:test03("args") -- table: 0x, args, test03
print("")
```

使用显式点号赋值定义函数时, 
- 如果函数不带参数, 那么两种调用方式没有区别.
- 如果带参数
  - 点号调用时, 参数与传入的参数相同
  - 冒号调用时, 第一个参数就是对象本身, 剩下的参数与传入参数相同



## 面向对象设计

在 lua 中, 需要使用原型模式来设计类, 一个通俗的解释就是在设计一个类时, 首先描述一个类的模板, 然后根据模板来创建对象.
受数据结构限制, lua 使用 `table` 来定义类模板类似于 javascript 中的 `object`.

```lua
-- 创建模板类结构
Class = {}

Class.print = function(self, args)
    print("hello, world")
end

-- 创建类对象
Class.new = function (self, args)
    obj = {}
    -- 为新对象设置模板/蓝图
    setmetatable(obj, self)
    return obj
end

-- 对象创建与使用
obj = Class:new()
obj:func()

```

** 约定 **
- 在定义类型时, 统一使用点号定义, 并且显式注明 `self`.
- 在调用函数时, 统一使用冒号调用.

## 基本知识与API

- lua 数组下标从 1 开始.
- 数组长度: `#arr`.
- 删除元素: `table.remove(tbl, key)`.
- 末尾增加元素: `arr[#arr+1] = value`.
- 插入元素: `table.insert(tbl, value)`
- for 循环(闭区间): `for i = 1, #arr do body end`.
- for 循环: `for idx, value in ipairs(arr) do body end`.


## 数据类型

- nil.
- boolean. false 和 nil 为 false, 其他值为 true.
- number. double 类型变量.
- string. 单引号, 双引号和 `[[]]`
- function.
- userdata.
- thread.
- table. 可以是字典, 也可用作数组, 索引默认从1开始. 通过pairs和ipairs进行遍历, 前者遍历所有的 key, 后者只遍历值大于等于 1 的 key.

判断数据类型使用 `type(val)`, 返回对应类型的字符串.

