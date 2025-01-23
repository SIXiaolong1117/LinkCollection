<script setup lang="ts">
defineProps<{ Link: string }>();
</script>

<template>
    <div class="avatar">
        <img :src="Link" alt="Avatar" />
    </div>
</template>

<style scoped>
.avatar {
    width: 8em;
    height: 8em;
    border-radius: 50%;
    overflow: hidden;
    display: flex;
    align-items: center;
    justify-content: center;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.avatar img {
    width: 100%;
    height: 100%;
    object-fit: cover;
}

@media screen and (max-width: 768px) {
    .avatar {
        width: 40vw;
        height: 40vw;
    }
}
</style>
