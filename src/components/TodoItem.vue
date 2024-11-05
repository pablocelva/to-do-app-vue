<template>
    <li :class="{ completed: todo.completed }">
      <input type="checkbox" :checked="todo.completed" @change="toggleComplete" />
      {{ todo.text }}
      <button @click="$emit('deleteTodo')">Eliminar</button>
    </li>
  </template>
  
  <script>
  export default {
    props: ["todo"],
    methods: {
      toggleComplete() {
      this.$emit('toggleComplete', this.todo.id); // Emitir el id
      }
    }
};
  </script>
  
  <style>
  /* Similar al estilo anterior */
  </style>
  