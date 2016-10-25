# action

action在实际的编码中可以理解为一个函数，通过`store.dispatch()`发起，返回一个固定格式的对象，如下所示：

```
const ADD_TODO = 'ADD_TODO';
function addTodo(text) {
  return {
    type: ADD_TODO,
    text
  }
}
```

每个action返回的格式都必须包含一个type，type为reducer指明了处理的内容。在以上代码中，我们设置type为一个静态变量，保证type为不可变的内容并便于维护。

## 注意

由于action本质还是一个js函数，对于`对象类型`的参数，如果使用同一个对象js会指向同一堆内存。我们还是应该持谨慎态度，建议使用以下规范：

1. 对象层级尽量简单，我们推荐使用单层结构，也有一些js库专门提供数据扁平化方案。
2. 在使用时，请进行深复制，这样可以避免

