<script setup lang="ts">
defineProps<{ Link: string }>();
</script>

<template>
    <div class="avatar-back">
    <div class="avatar">
        <img :src="Link" />
    </div>
    </div>
</template>

<style scoped>
.avatar {
    z-index: 2;
    margin-top: 4em;
    margin-bottom: 4em;
    width: 8em;
    height: 8em;
    border-radius: 50%;
    overflow: hidden;
    display: flex;
    align-items: center;
    justify-content: center;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.5);
    transform: rotate(0deg) rotateY(0deg) scale(1) !important;
    transition: transform 0.5s ease-in-out !important;
}

.avatar:hover {
    transform: rotate(360deg) rotateY(360deg) scale(2.5) !important;
    transition: transform 0.5s ease-in-out !important;
}

.avatar-back {
    z-index: 1;
    /* margin-top: -16em; */
    height: 16em;
    width: 35em;
    font-size: 14px;
    display: flex;
    justify-content: center;
    align-items: center;
    /* overflow: hidden; */
    border-radius: 8px;
    background-image: url("/avatar-back.jpg");
    background-repeat: no-repeat;
    background-position: center center;
    background-size: cover;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.5);
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
        margin-top: 0;
        margin-bottom: 0;
    }

    .avatar:hover {
        transform: rotate(360deg) rotateY(360deg) scale(1.4) !important;
        transition: transform 0.5s ease-in-out !important;
    }

    .avatar-back {
        /* display: none; */
        width: 70vw;
        height: 50vw;
    }
}
</style>
