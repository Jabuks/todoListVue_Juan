<template>
  <div id="app">
    <TodoBoard
      :todos="todos"
      @addTodo="addTodo"
      @deleteTodo="deleteTodo"
    />
  </div>
</template>

<script>
import TodoBoard from './components/TodoBoard.vue';

export default {
  name: 'App',
  components: {
    TodoBoard
  },
  data() {
    return {
      todos: []
    };
  },
  methods: {
    addTodo(todoData) {
      const newTodo = {
        id: Date.now(),
        title: todoData.title,
        creationDate: new Date().toISOString().substring(0, 10),
        dueDate: todoData.dueDate,
        complete: false
      };
      this.todos.push(newTodo);
    },
    deleteTodo(todoId) {
      this.todos = this.todos.filter(todo => todo.id !== todoId);
    }
  }
};
</script>

<style scoped>
#app {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
  background-color: #f5f5f5;
}
</style>
