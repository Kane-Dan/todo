<script setup>
import TaskCreateForm from "@/components/TaskCreateForm.vue"
import TodoList from "@/components/Todolist.vue"
import { ref } from "vue"
// создание прееменной для обновления  todolist
const updater = ref(false)
const update = () => {
    updater.value = !updater.value
}
</script>

<template>
    <div class="container">
        <div class="header">
            Адаптируй своё время
        </div>
        <div class="content">

            <TaskCreateForm @created="update" />
            <hr />

            <TodoList :updater="updater" />

        </div>
        <div class="footer"></div>
    </div>
</template>

<style scoped>
.container {
    height: 100vh;
    width: 100%;
    max-width: 1300px;
    margin: auto;
    padding: 10px;
    display: flex;
    flex-direction: column;
}

.header {
    padding: 10px;
    font-size: 30px;
    text-align: center;
    height: 120px;
}

.content {
    display: flex;
    overflow: hidden;
    flex-direction: column;
    height: 100%;
    padding: 10px 0px;
}

.footer {

    height: 100px;
    background-color: red;
}
</style>