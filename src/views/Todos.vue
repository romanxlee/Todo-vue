<template>
  <div>
    <h2>Todo-list</h2>
    <router-link to="/">Home</router-link>
    <hr>
    <AddTodo 
      @add-todo="addTodo"
    />
    <hr>
    <TodoList 
      v-if="todos.length"
      v-bind:todos="todos"
      @remove-todo="removeTodo"
    />
    <p v-else>Nothing to do...</p>
  </div>
</template>

<script>
import TodoList from '@/components/TodoList'
import AddTodo from '@/components/AddTodo'
export default {
  name: 'app',
  data() {
    return {
      todos: [
        {id: 1, title: 'Buy bread', completed: false},
        {id: 2, title: 'Buy butter', completed: false},
        {id: 3, title: 'Buy milk', completed: false},
      ]
    }
  },
  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter(t => t.id !== id)
    },
    addTodo(todo) {
      this.todos.push(todo)
    }
  },
  components: {
    TodoList, AddTodo
  }
}
</script>