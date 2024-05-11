<script setup>
import TodoForm from './TodoForm.vue';
import TodoList from './TodoList.vue';

</script>

<template>
    <div class="todo-app">
        <h1>To Do List</h1>
        <TodoForm></TodoForm>
        <TodoList></TodoList>
    </div>
</template>

<style scoped>
.todo-app {
    padding: 5vh;
    min-height: 100vh;
    width: 50vw;
    margin: 0 auto;
    background-color: #f7f9fc;
}
</style>