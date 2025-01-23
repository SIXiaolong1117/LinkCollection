<script setup lang="ts">
const props = defineProps<{ Email: string }>();

function emailto() {
    const emailLink = `mailto:${props.Email}`;
    window.location.href = emailLink;
}
</script>

<template>
    <el-button round @click="emailto">E-mail</el-button>
</template>

<style scoped>
.el-button {
    color: rgb(125, 125, 125);
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.el-button:hover {
    color: rgb(125, 125, 125);
    background-color: rgba(255, 255, 255, 1);
}
</style>
