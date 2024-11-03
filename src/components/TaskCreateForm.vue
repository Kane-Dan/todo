<script setup>
import { ref, onMounted } from 'vue'
import MyButton from './MyButton.vue';
import axios from 'axios';
const emit = defineEmits(['created'])
const title = ref(null)
const description = ref(null)
// созадние таски
const createTask = async () => {
    try {

        await axios.post('http://127.0.0.1:8000/tasks/create/', {
            title: title.value,
            description: description.value,
            user_id: 1
        });

    } catch (error) {
        console.error(error);
    }
    emit('created')
}

</script>



<template>

    <div class="form">
        
        <div class="addition">
            <h2>Я запомню что тебе сделать за день</h2>
            <h4>Заголовок твоей задачи ⬊</h4>
            <textarea name="textarea" style="resize: none;" rows="5" cols="30" minlength="3" 
                v-model="title" />
            <hr />
            <h4>Описание твоей задачи ⬊</h4>
            <textarea name="textarea" style="resize: none;" rows="5" cols="30" minlength="3" 
                v-model="description" />
        </div>
        <div class="pt-3">
            <MyButton @click="createTask">
                create
            </MyButton>
        </div>
    </div>

</template>



<style scoped>
.form {
    box-shadow: 0px 0px 23px 0px rgba(0, 0, 0, 0.1);
    padding: 10px;
    border-radius: 10px;
    text-align: center;
    /* background-color: rgb(41, 41, 41) ; */
    background-color: whitesmoke;
    color: black;
    display: flex;
}

.addition {
    width: 100%;
    height: 100%;
}

textarea {
    width: 90%;
    border-radius: 10px;
    padding: 5px;
}
.pt-3{
    display: flex;
    flex-direction: column-reverse;
    min-width: 100px;
}
h4{
    display: flex;
}
</style>