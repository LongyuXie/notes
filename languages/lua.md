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

## 面向对象设计

在 lua 中, 需要使用原型模式来设计类, 一个通俗的解释就是在设计一个类时, 首先描述一个类的模板, 然后根据模板来创建对象.
受数据结构限制, lua 使用 `table` 来定义类模板类似于 javascript 中的 `object`.

```lua
-- 创建模板类结构
Class = {}

Class:print (args)
    print("hello, world")
end

-- 创建类对象
Class:new (args)
    obj = {}
    -- 为新对象设置模板/蓝图
    setmetatable(obj, self)
    return obj
end

-- 对象创建与使用
obj = Class:new()
obj:func()

```



