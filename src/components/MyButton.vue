<script setup>
</script>

<template>
    <div class="btn">
        <slot />
    </div>
</template>

<style scoped>
.btn{
    
    background-color: black;
    color: white;
    text-align: center;
    padding: 0.2rem 0.4rem;
    border-radius: 10px;
    max-width: 100px;
}

</style>