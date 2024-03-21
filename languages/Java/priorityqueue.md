## 优先队列

Java中的优先队列(PriorityQueue<>)是一个小顶堆, 其堆顶元素是优先级最大的元素.
举个例子, 例如`PriorityQueue<Integer>`, 那么对顶元素就是队列中的最小值.
<!-- 如果需要最小堆或者需要自定义优先级选择 -->

### 常用接口

- `Q.poll()`: 移出堆顶元素
- `Q.offer()`: 增加一个元素
- `Q.peek()`: 返回堆顶元素

### 自定义比较函数

如果需要自定义比较函数, 那么在创建对象时需要传入一个`Comparator<>`对象, 用于比较
优先级, 堆顶元素是优先级最大的.
- 如果`compare(a, b)`返回正数, 那么 `a > b`
- 如果返回0, 则 `a = b`
- 否则 `a < b `


```java
var queue = new PriorityQueue<int[]>(new Comparator<int[]>() {

    public int compare(int[] a, int[] b) {
        return a[0] == b[0] ? a[1] - b[1] : a[0] - b[0]
    }
})
```

如果要求堆顶元素是最大值, 也就是降序排列, 那么可以使用 `Comparator.reverseOrder()`