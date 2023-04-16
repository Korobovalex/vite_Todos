<template>
  <main>
      <h1>Текущие задачи</h1>
      <todo-creator
          @create-todo="createTodo"
      />
      <ul v-if="todoList.length > 0" class="todo-list">
          <todo-item
              v-for="(todo, index) in todoList"
              :key="todo.id"
              :todo="todo"
              :index="index"
              @toggle-complete="toggleTodoComplete"
          />
      </ul>
      <p class="todos-msg" v-else>
          <Icon icon="noto-v1:sad-but-relieved-face" />
          <span>У вас еще нет ни одной записи! Создайте новую!</span>
      </p>
  </main>
</template>

<script setup>
import TodoCreator from "@/components/TodoCreator.vue";
import { ref } from "vue";
import { uid } from 'uid';
import { Icon } from "@iconify/vue";
import TodoItem from "../components/TodoItem.vue";

const todoList = ref([]);

const createTodo = (todo) => {
    todoList.value.unshift({
        id: uid(),
        todo,
        isCompleted: false,
        isEditing: false,
    });
};

const toggleTodoComplete = (todoIdx) => {
    todoList.value[todoIdx].isCompleted = !todoList.value[todoIdx].isCompleted;
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

    .todo-list {
        display: flex;
        flex-direction: column;
        align-items: center;
        margin-top: 16px;
        gap: 12px;
        list-style: none;
    }

    .todos-msg {
        display: flex;
        align-items: center;
        justify-content: center;
        gap: 8px;
        margin-top: 16px;
        font-size: 13px;
    }

}
</style>