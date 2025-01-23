<script setup lang="ts">
const props = defineProps<{ Msg: string }>();

function sharePage() {
    if (navigator.share) {
        navigator.share({
            title: document.title,
            text: props.Msg,
            url: window.location.href,
        })
            .then(() => console.log('分享成功'))
            .catch((error) => console.error('分享失败:', error));
    } else {
        alert('当前浏览器不支持分享功能。');
    }
}
</script>

<template>
    <el-button circle class="floating-share-button" @click="sharePage">
        <font-awesome-icon :icon="['fas', 'share-from-square']" size="2x" class="share-icon" />
    </el-button>
</template>

<style scoped>
.floating-share-button {
    padding: 0;
    width: 4em !important;
    height: 4em;
    position: fixed;
    top: 2em;
    right: 2em;
    z-index: 1000;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
    background-color: rgba(255, 255, 255, 0.5);
    border: #00000000;
}

.share-icon {
    color: rgba(0, 0, 0, 0.5);
}

.el-button:hover {
    background-color: rgba(255, 255, 255, 0.6);
}

@media screen and (max-width: 768px) {
    .floating-share-button {
        width: 3em !important;
        height: 3em;
        top: .5em;
        right: 1em;
    }
}
</style>
