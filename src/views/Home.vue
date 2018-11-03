<template>
  <div class="home">
    <TodoList></TodoList>
    <TodoForm></TodoForm>
  </div>
</template>

<script>
// @ is an alias to /src
import TodoForm from '@/components/TodoForm.vue';
import TodoList from '@/components/TodoList.vue';

export default {
  name: 'home',
  components: {
    TodoList,
    TodoForm,
  },
};
</script>
