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

每个action返回的格式都必须包含一个type，type为reducer指明了处理的内容。在以上代码中，我们设置type为一个静态变量，保证type为不可变的内容并便于区分。



