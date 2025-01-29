<script setup>
import TodoItem from '@/components/TodoItem.vue';
import TodosCreator from '@/components/TodosCreator.vue';

import { uid } from 'uid';
import { ref } from 'vue';

  const todoList = ref([])

  const createTodo = (todo) => {
    console.log('Received event with:', todo);
    todoList.value.push({
      id: uid(),
      todo,
      iscompleted: false,
      isEditing: false,
    })
    console.log('Updated todoList:', todoList.value); 
  }
</script>

<template>
  <main>
    <h1>Create  Todo</h1>
    <TodosCreator @create-todo="createTodo"/>
    <TodoItem v-for="todo in todoList"/>
  </main>
</template>

<style lang="scss" scoped>
  main {
  display: flex;
  flex-direction: column;
  max-width: 500px;
  width: 100%;
  margin: 0 auto;
  padding: 40px 16px;

  h1 {
    margin-bottom: 16px;
    text-align: center;
  }
}
</style>
