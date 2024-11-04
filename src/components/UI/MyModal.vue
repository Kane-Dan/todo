<script setup>
import { ref } from 'vue'
import MyButton from './MyButton.vue';

const isVisible = ref(false)

const open = () => {
    isVisible.value = true
}

const close = () => {
    isVisible.value = false
}

defineExpose({ open, close })
</script>

<template>
    <div class="popup_modal" v-if="isVisible" @click.stop.pervent.self="close">
        <div class="window">
            <div class="close_btn">
                <MyButton @click.stop.pervent.self="close">close</MyButton>
            </div>
            <slot />
        </div>
    </div>
</template>

<style scoped>
.popup_modal {
    height: 100%;
    width: 100%;
    position: absolute;
    top: 0;
    left: 0;
    z-index: 100;
    background-color: rgba(255, 255, 255, 0.5);
    display: flex;
    align-items: center;
    justify-content: center;
}

.window {
    background-color: white;
    padding: 10px;
    max-width: 1000px;
}
.close_btn{
    display: flex;
    justify-content: end;
}
</style>