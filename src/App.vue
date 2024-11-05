<template>
  <div class="container">
    <h1>To Do List Vue</h1>
    <TodoForm @addTodo="addTodo" />
    <TodoList :todos="todos" @toggleComplete="toggleComplete" @deleteTodo="deleteTodo" />
  </div>
</template>

<script>
import TodoList from './components/TodoList.vue';
import TodoForm from './components/TodoForm.vue';

export default {
  name: 'App',
  components: {
    TodoList,
    TodoForm
  },
  data() {
    return {
      todos: []
    };
  },
  methods: {
    addTodo(text) {
      this.todos.push({ id: Date.now(), text, completed: false });
    },
    toggleComplete(id) {
      const todo = this.todos.find(t => t.id === id);
      if (todo) todo.completed = !todo.completed;
    },
    deleteTodo(id) {
      this.todos = this.todos.filter(t => t.id !== id);
    }
  }
};
</script>

<style>
/* src/app/app.component.css */
.container {
  text-align: center;
  max-width: 400px;
  margin: auto;
  font-family: Arial, sans-serif;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 8px;
  border-bottom: 1px solid #ddd;
}

button {
  background-color: #f44336;
  color: white;
  border: none;
  padding: 5px;
  cursor: pointer;
}

button:hover {
  background-color: #d32f2f;
}

.completed {
  text-decoration: line-through;
}

</style>
