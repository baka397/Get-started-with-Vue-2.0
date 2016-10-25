1. # reducer


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

在此基础上，通常使用`switch`来匹配action的内容，如下：

```
const initialState = {
    todos: []
}
function todoApp(state = initialState, action) {
      switch(action.type){
        //case condition
        default:
            return state
      }
}
```

## 注意

和action一样，我们同样需要注意对象类型的数据，return时使用`Object.assign`将是个好的选择。

同时，在变更数组类型数据时，建议根据情况使用以下方法：

1. 删除数据时使用`splice`。
2. 更改某条数据时使用 `slice` 和`concat`拆分后拼接。

## 合并多个reducer



