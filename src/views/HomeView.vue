<template>
  <main>
      <h1>Текущие задачи</h1>
      <todo-creator @create-todo="createTodo" />
  </main>
</template>

<script setup>
import TodoCreator from "@/components/TodoCreator.vue";
import { ref } from "vue";
import { uid } from 'uid';

const todoList = ref([]);

const createTodo = (todo) => {
    todoList.value.unshift({
        id: uid(),
        todo,
        isCompleted: false,
        isEditing: false,
    });
};

</script>

<style lang="scss" scoped>
main {
    display: flex;
    flex-direction: column;
    width: 100%;
    max-width: 500px;
    margin: 0 auto;
    padding: 40px 16px;

    h1 {
        margin-top: 16px;
        text-align: center;
    }
}
</style>