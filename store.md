# store

和react中不同，在vue中我们通过另外的方法绑定store数据。

在vue中，需要创建一个额外的store模块以供组件调用，如官方示例：

```
import Vue from 'vue'
import Revue from 'revue'
import {createStore} from 'redux'
// create the logic how you would update the todos
import todos from './reducers/todos'
// create some redux actions
import actions from './actions'

// create a redux store
const reduxStore = createStore(todos)
// binding the store to Vue instance, actions are optional
const store = new Revue(Vue, reduxStore, actions)
// expose the store for your component to use
export default store
```

在组件中我们使用`this.$select`（react中使用）方法来选择对应的reducer数据，使用store.dispatch（react中直接绑定了 dispatch 方法在prop中）来

