<script setup>
import { ref, defineProps, onMounted } from 'vue'
import MyButton from './UI/MyButton.vue';
import axios from 'axios';
const emit = defineEmits(['update'])
const props = defineProps({
    taskId: { type: Number, default: null }
})

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

    } catch (e) {
        console.error(e);
    }
    emit('update')
}

const updateTask = async () => {
    try {
        await axios.put(`http://127.0.0.1:8000/tasks/update/${props.taskId}`, {
            title: title.value,
            description: description.value,
        });
    } catch (e) {
        console.error(e);
    }
    emit('updated')
}

const getTaskById = async () => {
    if (!props.taskId) {
        return
    } else {
        try {
            const res = await axios.get(`http://127.0.0.1:8000/tasks/${props.taskId}`)
            title.value = res.data.title
            description.value = res.data.description
        } catch (e) {
            console.error(e);
        }
    }
}

onMounted(() => {
    getTaskById()
})
</script>



<template>

    <div class="form">
        <div class="addition">
            <div class="text-center">
                <h2>Я запомню что тебе сделать за день</h2>
            </div>
            <h4>Заголовок твоей задачи ⬊</h4>
            <textarea class="title" name="title" style="resize: none;" rows="1" minlength="3" v-model="title" />
            <hr />
            <h4>Описание твоей задачи ⬊</h4>
            <textarea class="description" name="description" style="resize: none;" rows="5" minlength="3"
                v-model="description" />
        </div>
        <div class="create_btn_wrapper">
            <MyButton v-if="props.taskId" @click="updateTask">save</MyButton>
            <MyButton v-else @click="createTask">create</MyButton>
        </div>
    </div>

</template>



<style scoped>
textarea {
    border-radius: 10px;
    padding: 5px;
}

.title {
    width: 100%;
    max-width: 300px;
}

.description {
    width: 100%;
}


.form {
    box-shadow: 0px 0px 23px 0px rgba(0, 0, 0, 0.1);
    padding: 10px;
    border-radius: 10px;
    /* background-color: rgb(41, 41, 41) ; */
    background-color: whitesmoke;
    color: black;
    display: flex;
}

.addition {
    width: 100%;
    height: 100%;
}

.create_btn_wrapper {
    min-width: 100px;
    flex-direction: column-reverse;
    display: flex;
    /* overflow: hidden; */
}

h4 {
    display: flex;
}
</style>