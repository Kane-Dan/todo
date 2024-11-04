<script setup>
import axios from "axios"
import { ref, onMounted, watch } from 'vue'
import TheTask from "./TheTask.vue";
// получение обновления из Mainpage
const props = defineProps({
    updater: { type: Boolean }
})

// Вывод всех тасок
const todoList = ref(null)
const getTodoList = async () => {
    try {
        const response = await axios.get('http://127.0.0.1:8000/tasks/all');
        todoList.value = response.data;
    } catch (error) {
        console.error(error);
    }
}

// следит за переменной updater чтобы в момент изменения обновить gettodolist(функцию)
watch(() => props.updater, getTodoList)

onMounted(() => {
    getTodoList();
})
</script>


<template>
    <div class="todo_list_wrapper">
        <the-task v-for="task in todoList" :task="task" :key="task.id" @update="getTodoList" />
    </div>
</template>


<style scoped>
.todo_list_wrapper{
    box-shadow: 0px 0px 23px 0px rgba(0, 0, 0, 0.1);
    padding: 10px;
    border-radius: 10px;
    background-color: whitesmoke;
    color: black;
    overflow: auto;
}
</style>