<template>
    <form @submit.prevent="addTodo">
      <input type="text" v-model="text" placeholder="Añadir una tarea..." required />
      <button type="submit">Añadir</button>
    </form>
  </template>
  
  <script>
  export default {
    data() {
      return {
        text: ""
      };
    },
    methods: {
      addTodo() {
        if (this.text.trim()) {
          this.$emit("addTodo", this.text);
          this.text = "";
        }
      }
    }
  };
  </script>
  