<template>
  <div id="todo-list-example">
    <p>Your Todos</p>
    <ul v-for="todo in todos" :key="todo.id">
      <li>{{ todo.content }}</li>
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
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
