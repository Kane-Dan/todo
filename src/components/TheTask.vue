<script setup>
import { defineProps,defineEmits } from 'vue'
import MyButton from "./MyButton.vue";
import axios from 'axios';

const props = defineProps({
    task: { type: Object, default: null }
})

const emit = defineEmits(['update'])
// Кнопка измены
const editTask = () => {}
// Кнопка удаления
const deleteTask = async (id) => {
    try {
        await axios.delete(`http://127.0.0.1:8000/tasks/delete/${id}`);
    }catch (error) {
        console.error(error);
    }
    emit('update')
}
</script>

<template>
   <div class="task_container">
        <div class="task"> 
            Заголовок
            <textarea name="textarea" style="resize: none;"rows="5" cols="30" minlength="3" v-model="task.title"/>
            <hr />
            Описание
            <textarea name="textarea" style="resize: none;"rows="5" cols="30" minlength="3"  v-model="task.description" />
        </div>
        <div class="btn_wrapper">
            <MyButton @click="deleteTask(task.id)"class="mb-1">delete</MyButton>
            <MyButton @click="editTask(task.id)"class="mt-1">edit</MyButton>
        </div>
    </div>
</template>

<style scoped>
.task_container{
    box-shadow: 0px 0px 10px 0px rgba(0, 0, 0, 0.2) inset;
    border-radius: 10px;
    padding: 10px;
    margin: 10px ;
    display: flex;
    overflow: auto;
}
.task {
    width: 100%;
    height: 100%;
}
.btn_wrapper{
    min-width: 100px;
    display: flex;
    flex-direction: column;
    padding:0 10px;
    justify-content: space-between;
}
textarea{
    width: 95%;
    border-radius: 10px;
    padding: 10px;
    
}
</style>