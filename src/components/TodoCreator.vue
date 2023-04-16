<template>
    <div class="input-wrap" :class="{ 'input-invalid' : todoState.invalid }">
        <input type="text" v-model="todoState.todo" @keyup.enter="createTodo">
        <the-button @click="createTodo">Создать</the-button>
    </div>
    <p v-show="todoState.invalid" class="err-msg">
        {{ todoState.errMsg }}
    </p>
</template>

<script setup>
import TheButton from "@/components//TheButton.vue";
import {reactive } from "vue";

const emit = defineEmits(['create-todo']);
const todoState = reactive({
    todo: '',
    invalid: false,
    errMsg: '',
});

const createTodo = () => {
    todoState.invalid = false;
    if (todoState.todo !== '') {
    emit('create-todo', todoState.todo);
    todoState.todo = '';
    return;
    }
    todoState.invalid = true;
    todoState.errMsg = 'Введите текст задачи.';
}
</script>

<style lang="scss" scoped>
.input-wrap {
    display: flex;
    border: 2px solid #41b080;
    transition: 0.25s;

    &.input-invalid {
        background-color: #ff0000;
    }

    &:focus-within {
        box-shadow: 0 -4px 6px -1px rgb(0 0 0 / 0.1), 0 -2px 4px -2px rgb(0 0 0 / 0.1);
    }

    input {
        width: 100%;
        padding: 8px 16px;
        border: none;

        &:focus {
            outline: none;
        }
    }
}

.err-msg {
    margin-top: 8px;
    font-size: 12px;
    font-weight: 500;
    text-align: center;
    color: #f00;
}
</style>