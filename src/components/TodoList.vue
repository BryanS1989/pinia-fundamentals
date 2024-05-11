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

const { toggleCompleted } = store;
</script>

<template>
    <div v-for="todo in todoList" :key="todo.id" class="item">
        <div class="content">
            <span :class="{ completed: todo.completed }">{{ todo.item }}</span> 
            <span @click.stop="toggleCompleted(todo.id)" class="check-todo">&#10004;</span>
        </div>
    </div>
</template>

<style scoped>
.completed {
    text-decoration: line-through;
}
.check-todo {
    cursor: pointer;
    padding-left: 1rem;
    color:#00ff00
}
</style>