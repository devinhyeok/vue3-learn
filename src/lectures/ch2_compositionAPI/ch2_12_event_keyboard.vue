<template>
  <div>
    <!--enter: "enter" 키를 입력했을때 수식어-->
    <input type="text" @keyup.enter="addTodo" @keydown.delete="removeTodo" />
    <ul>
      <li v-for="(todo, index) in todos" :key="index">
        {{ todo }}
      </li>
    </ul>
  </div>
</template>

<script>
import { reactive } from 'vue';

export default {
  setup() {
    const todos = reactive([]);

    const addTodo = (event) => {
      todos.push(event.target.value);
      event.target.value = '';
      event.target.focus();
    }

    const removeTodo = (event) => {
      todos.pop();
    }
    return { todos, addTodo, removeTodo };
  },
};
</script>

<style scoped>

</style>