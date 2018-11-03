<template>
  <div id="todo-list-example">
    <p>Your Todos</p>
    <p>Next Todo ID is: {{ nextTodoId }}</p>
    <p>New Todo Content is: {{ newTodoContent }}</p>
    <ul id="todosList">
      <li v-for="todo in todos" :key="todo.id">
        <input type="checkbox">
        <span>{{ todo.content }}</span>
        <button v-on:click="editTodo(todo.id)">EDIT</button>
        <button v-on:click="deleteTodo(todo.id)">DELETE</button>
      </li>
    </ul>
    <input v-model="newTodoContent" placeholder="eg. Walk the dog">
    <input type="submit" v-on:click="createTodo(newTodoContent)">
  </div>
</template>

<script>
export default {
  name: 'TodoList',
  data() {
    return {
      nextTodoId: 4,
      newTodoContent: '',
      todos: [
        {
          id: 1,
          content: 'this is my first todo',
          isCompleted: false,
        },
        {
          id: 2,
          content: 'here is a second todo',
          isCompleted: false,
        },
        {
          id: 3,
          content: 'and a third todo',
          isCompleted: true,
        },
      ],
    };
  },
  methods: {
    toggleCompleted(id) {
      console.log(`toggling isCompleted for todo with id ${id}`);
    },
    createTodo(currentTodoContent) {
      console.log(currentTodoContent);
      this.nextTodoId = this.nextTodoId + 1;
      this.todos.push({
        id: this.nextTodoId,
        content: currentTodoContent,
        isCompleted: false,
      });
      // add 1 to counter for id's
    },
    editTodo(id) {
      console.log(`edit todo with id ${id}`);
    },
    deleteTodo(id) {
      console.log(`deleting todo with id ${id}`);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.completed {
  text-decoration: line-through
}
</style>
