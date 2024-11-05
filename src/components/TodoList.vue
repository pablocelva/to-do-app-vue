<template>
    <ul>
      <TodoItem
        v-for="todo in todos"
        :key="todo.id"
        :todo="todo"
        @toggleComplete="toggleComplete"
        @deleteTodo="deleteTodo(todo.id)"
      />
    </ul>
  </template>
  
  <script>
  import TodoItem from './TodoItem.vue';
  
  export default {
    components: { TodoItem },
    props: ['todos'],
    methods: {
      toggleComplete(id) {
      this.$emit('toggleComplete', id);
    },
    deleteTodo(id) {
      this.$emit('deleteTodo', id);  // Emitir evento hacia el padre
    }
    }
  };
  </script>

<style>
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