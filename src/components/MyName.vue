<script setup lang="ts">
defineProps<{ Name: string }>();
</script>

<template>
    <div>
        <div class="MyName"><b> {{ Name }} </b></div>
        <div>ヽ(´ー｀)ﾉ</div>
    </div>
</template>

<style scoped>
.MyName {
    font-size: 18px;
}
</style>
