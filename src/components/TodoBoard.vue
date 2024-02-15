<template>
 <header class="header">My Todos</header>
        <div class="todo-board">
            <form class="add-todo-container" @submit.prevent="onAddTodo">
                <input class="add-todo-input" v-model="newTodoTitle" type="text" placeholder="Add new..." />
                <input class="todo-date-due" v-model="newTodoDueDate" type="date" placeholder="Due date" />
                <button class="add-todo-button" type="submit">Add</button>
            </form>
            <TodoItems class="todo-item"
                v-for="todo in todos"
                :key="todo.id"
                :todo="todo"
                @deleteTodo="onDeleteTodo"
            />
        </div>
</template>
  
  <script>
  import TodoItems from './TodoItems.vue';
  
  export default {
    components: {
      TodoItems
    },
    props: ['todos'],
    data() {
      return {
        newTodoTitle: '',
        newTodoDueDate: ''
      };
    },
    methods: {
      onAddTodo() {
        if (this.newTodoTitle.trim() && this.newTodoDueDate) {
          this.$emit('addTodo', {
            title: this.newTodoTitle,
            dueDate: this.newTodoDueDate
          });
          this.newTodoTitle = '';
          this.newTodoDueDate = '';
        } else {
          alert('Please enter both title and due date.');
        }
      },
      onDeleteTodo(todoId) {
        this.$emit('deleteTodo', todoId);
      }
    }
  };
  </script>

<style scoped>


.header{
  font-size: 2rem;
  margin-bottom: 1rem;
}

.todo-board {
  width: 100%;
  max-width: 600px;
  background-color: #fff;
  padding: 2rem;
  margin: 1rem;
  border-radius: 8px;
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
  display: flex;
  flex-direction: column;
  align-items: center;
}

.add-todo-container {
  width: 100%;
  display: flex;
  margin-bottom: 2rem;
}

.add-todo-input {
  flex-grow: 1;
  padding: 0.5rem;
  margin-right: 1rem;
  border: 1px solid #ccc;
  border-radius: 0.25rem;
}

.add-todo-button {
  padding: 0.5rem 1rem;
  background-color: #007bff;
  margin-right: 1rem;
  margin-left: 1rem;
  border: none;
  border-radius: 1rem   ;
  color: white;
  cursor: pointer;
}

.add-todo-button:hover {
  background-color: #0056b3;
}

.todo-date-due {
  background-color: #e9ecef;
  border-radius: 0.25rem;
  padding: 0.25rem 0.5rem;
  margin-left: 0.5rem;
  font-size: 0.875rem;
}

</style>


  
  