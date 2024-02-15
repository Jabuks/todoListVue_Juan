<template>
    <div class="todo-item">
      <input class="todo-item-checkbox" type="checkbox" v-model="todo.complete">
      <span class="todo-text" todo-item-text>{{ todo.title }} - created on: {{ todo.creationDate }} - due by: {{ todo.dueDate }}</span>
      <button class="todo-item-delete" @click="onDeleteTodo(todo.id)">X</button>
    </div>
  </template>
  
  <script>
  export default {
    props: ['todo'],
    methods: {
      onDeleteTodo(todoId) {
        this.$emit('deleteTodo', todoId);
      }
    }
  };
  </script>

<style scoped>
.todo-item {
  width: 100%;
  background-color: #f8f8f8;
  border: 1px solid #ccc;
  border-radius: 4px;
  display: flex;
  align-items: center;
  padding: 1rem;
  margin-bottom: 1rem;
}

.todo-text {
  margin-right: 1rem;
  flex-grow: 1;
}
.todo-item-checkbox {
  margin-right: 0.5rem;
}

.todo-item-text {
  flex-grow: 1;
  margin-right: 0.5rem;
}

.todo-item-delete {
  background-color: #dc3545;
  border: none;
  border-radius: 0.25rem;
  color: white;
  padding: 0.25rem 0.5rem;
  cursor: pointer;
}
.todo-item-delete:hover {
  background-color: #c82333;
}
</style>
  
  
