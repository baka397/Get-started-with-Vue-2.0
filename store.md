# store

和react中不同，在vue中我们通过另外的方法绑定store数据。

在vue中，需要创建一个额外的store模块以供组件调用（react中使用`Provider`组件来传递store），如官方示例：

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

在组件中我们使用`this.$select`（react中使用 `connect`和`propMap`函数来绑定组件）方法来选择对应的reducer数据，使用`store.dispatch`（react中直接绑定了 `dispatch`方法在prop中）来调用action函数，如官方示例：

```
import store from './store'
import * as todoActions from './actions/todo'

export default {
  data() {
    return {
      todo: '',
      todos: this.$select('todos')
      //=> subscribe state.todos to vm.todos
      // if prop is not in top level
      // do this.$select('todos as path.to.todos')
    }
  },
  methods: {
    addTodo() {
      store.dispatch({type: 'ADD_TODO', this.todo})
      // or use the actionCreator
      store.dispatch(todoActions.addTodo(this.todo))
      // also equal to: (if you binded actions when creating the store)
      const {addTodo} = store.actions
      store.dispatch(addTodo(this.todo))
    }
  }
}
```

## 注意

由于`revue`不支持vue 2.0，所以我们修改reven并放入lib中。

