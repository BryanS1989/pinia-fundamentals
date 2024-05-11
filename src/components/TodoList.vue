<script setup>
import { useTodoListStore } from "@/stores/todoList";
import { storeToRefs } from "pinia";

const store = useTodoListStore();

/*
    storeToRefs allow us to bring in properties
    from our store ensuring the reactivity for 
    each property. Creates refs for each property
*/
const { todoList } = storeToRefs(store); // storeToRefs lets todoList keep reactivity:

const { toggleCompleted, deleteTodo } = store;
</script>

<template>
    <div v-for="todo in todoList" :key="todo.id" class="item">
        <div class="content">
            <span :class="{ completed: todo.completed }">{{ todo.item }}</span> 
            <span>
                <span @click.stop="toggleCompleted(todo.id)" class="check-todo">&#10004;</span>
                <span @click="deleteTodo(todo.id)" class="delete-todo">&#10006;</span>
            </span>
        </div>
    </div>
</template>

<style scoped>
span {
    margin: 0 10px;
    cursor: pointer;
}
.item {
    display: flex;
    justify-content: center;
}
.content {
    display: flex;
    font-size: 1.5em;
    justify-content: space-between;
    width: 80vw;
    padding: 5px;
}
.completed {
    text-decoration: line-through;
}
.check-todo {
    cursor: pointer;
    color:#00ff00;
    font-size: 1.5rem;
}
.delete-todo {
    cursor: pointer;
    color:#ff0000;
    font-size: 1.5rem;
}
</style>