<template>
  <div id="todo-list">
    <p>Your Todos</p>
    <ul id="todos-list">
      <li v-for="todo in todos" :key="todo.id" :id="'li-' + todo.id">
        <input type="checkbox" class="incomplete" :id="'checkbox-' + todo.id">
        <span class="todo-content" :id="'span-' + todo.id">{{ todo.content }}</span>
        <button v-on:click="editTodo(todo.id)" :id="'btn-edit-' + todo.id">EDIT</button>
        <button v-on:click="deleteTodo(todo.id)" :id="'btn-delete-' + todo.id">DELETE</button>
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
      // counter increments every time a new todo is created, starting with 1
      todoIdCounter: 3,
      // tracks value of the input field every time it changes
      newTodoContent: '',
      // list of todos
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
    // toggle checked/unchecked and strikethrough
    toggleCompleted(id) {
      console.log(`toggling isCompleted for todo with id ${id}`);
    },

    // create a new todo
    createTodo(currentTodoContent) {
      console.log(currentTodoContent);
      this.todoIdCounter = this.todoIdCounter + 1;
      this.todos.push({
        id: this.todoIdCounter,
        content: currentTodoContent,
        isCompleted: false,
      });
      this.newTodoContent = '';
    },

    // edit an existing todo
    editTodo(todoId) {
      for (let i = 0; i < this.todos.length; i += 1) {
        if (this.todos[i].id === todoId) {
          // id names
          let itemId = `li-${todoId}`;
          let checkboxId = `checkbox-${todoId}`;
          let spanId = `span-${todoId}`;
          let editBtnId = `btn-edit-${todoId}`;
          let deleteBtnId = `btn-delete-${todoId}`;

          // current element variables
          let currentItem = document.getElementById(itemId);
          let currentCheckbox = document.getElementById(checkboxId);
          let currentSpan = document.getElementById(spanId);
          let currentEditBtn = document.getElementById(editBtnId);
          let currentDeleteBtn = document.getElementById(deleteBtnId);

          // data variables
          const currentTodoContent = this.todos[i].content;

          // logging elements
          console.log(currentItem);
          console.log(currentCheckbox);
          console.log(currentSpan);
          console.log(currentEditBtn);
          console.log(currentDeleteBtn);

          // dom manipulation - removing element;
          currentItem.removeChild(currentEditBtn)
          currentItem.removeChild(currentDeleteBtn)
          currentItem.removeChild(currentSpan);

          // new elements
          const input = document.createElement('input');
          input.setAttribute('value', currentTodoContent);
          const submitBtn = document.createElement('button');
          submitBtn.innerHTML = 'SUBMIT';
          const cancelBtn = document.createElement('button');
          cancelBtn.innerHTML = 'CANCEL';

          // dom manipulation - append new elements to dom
          currentItem.appendChild(input);
          currentItem.appendChild(submitBtn);
          currentItem.appendChild(cancelBtn);
        }
      }
    },

    // delete an existing todo
    deleteTodo(todoId) {
      for (let i = 0; i < this.todos.length; i += 1) {
        if (this.todos[i].id === todoId) {
          this.todos.splice(i, 1);
        }
      }
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
li {
  list-style: none;
  margin-left: -40px;
}

.complete {
  text-decoration: line-through
}
</style>
