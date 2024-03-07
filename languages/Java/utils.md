## 常用方法


### Array

- 获取数组长度: `array.length`

### Collection

- 返回一个空列表: `Collections.emptyList()`, 不可以直接返回`{}`
- 判断数组相等: `Arrays.equals(a1, a2)`

### String

- 获取字符串长度: `s.length()`
- for-each遍历字符串: `for (var c : s.toCharArray())`, 不可以直接`for (var c : s)`
- 按索引获取字符: `char c = s.charAt(index)`
- char类型是2字节数据, 存储字符编码, 可以直接相加减: `assert(('b'-'a') == 1)`