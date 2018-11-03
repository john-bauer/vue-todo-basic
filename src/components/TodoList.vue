<template>
  <div id="todo-list-example">
    <p>Your Todos</p>
    <ul v-for="todo in todos" :key="todo.id">
      <li>
        <span>{{ todo.content }}</span>
        <button v-on:click="toggleCompleted(todo.id)">TOGGLE COMPLETED</button>
        <button v-on:click="editTodo(todo.id)">EDIT</button>
        <button v-on:click="deleteTodo(todo.id)">DELETE</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'TodoList',
  data() {
    return {
      todos: [
        {
          id: 1,
          content: 'this is my first todo',
        },
        {
          id: 2,
          content: 'here is a second todo',
        },
        {
          id: 3,
          content: 'and a third todo',
        },
      ],
    };
  },
  methods: {
    toggleCompleted(id) {
      console.log(`toggling isCompleted for todo with id ${id}`)
    },
    editTodo(id) {
      console.log(`editing todo with id ${id}`);
    },
    deleteTodo(id) {
      console.log(`deleting todo with id ${id}`);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
