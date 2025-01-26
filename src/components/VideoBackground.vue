<script setup lang="ts">
</script>

<template>
    <video class="video-background" autoplay loop muted playsinline>
        <source
            src="https://cdn.fastly.steamstatic.com/steamcommunity/public/images/items/2861720/85882f90ad8ca69467610883a9fa95ecc2f071ab.webm"
            type="video/webm" />
        Your browser does not support the video tag.
    </video>
</template>

<style scoped>
.video-background {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
    z-index: -1000;
    opacity: 0.2;
}
</style>
