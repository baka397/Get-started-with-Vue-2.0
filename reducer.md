# reducer

reducer是一个数据处理函数，这意味着一个reducer函数必须满足**输入值固定，则输出值固定**。

当使用`store.dispatch`执行一个action后，reducer函数会被触发，触发时会传递两个参数`state`和`action`。`state`是之前的状态，`action`是action函数的值。如下

```
function todoApp(state, action) {
  if (typeof state === 'undefined') {
    return initialState
  }

  // For now, don't handle any actions
  // and just return the state given to us.
  return state
}
```

通常，我们还需要指定reducer的缺省值，如下：

```
const initialState = {
  todos: []
}
function todoApp(state = initialState, action) {
  // For now, don't handle any actions
  // and just return the state given to us.
  return state
}
```

