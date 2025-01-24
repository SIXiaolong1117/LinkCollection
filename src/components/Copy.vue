<script setup lang="ts">
import { computed } from 'vue';
import { ref } from 'vue';

const { Copy, PlatformsName, Description, Icon, IconFamily, SvgIcon } = defineProps<{
    Copy: string;
    PlatformsName?: string;
    Description?: string;
    Icon?: string;
    IconFamily?: string;
    SvgIcon?: string;
}>();

const SocialPlatforms = computed(() => {
    const platform = {
        platformsName: 'Unknown',
        iconfamily: 'fas',
        icon: 'square-full',
        isCustomSvgIcon: false
    };

    if (PlatformsName) {
        platform.platformsName = PlatformsName;
    }
    if (SvgIcon) {
        platform.isCustomSvgIcon = true;
        platform.icon = SvgIcon;
    } else if (Icon) {
        platform.icon = Icon;
    }
    if (IconFamily) {
        platform.iconfamily = IconFamily;
    }

    return platform;
});

// 复制链接
const copiedRef = ref(false);
function copyLink() {
    navigator.clipboard.writeText(Copy).then(() => {
        copiedRef.value = true;
        setTimeout(() => {
            copiedRef.value = false;
        }, 2000);
    }).catch(err => {
        console.error('拷贝失败: ', err);
    });
}
</script>

<template>
    <div class="main-box">
        <el-button class="button" plain @click="copyLink">
            <div class="SocialIcon">
                <template v-if="SocialPlatforms.isCustomSvgIcon">
                    <div class="custom-svg" v-html="SocialPlatforms.icon"></div>
                </template>
                <template v-else>
                    <font-awesome-icon :icon="[SocialPlatforms.iconfamily, SocialPlatforms.icon]" size="2x" />
                </template>
            </div>
            <div class="SocialDetail">
                <div class="SocialDetail-inner"><b>{{ PlatformsName }}</b></div>
                <div class="SocialDetail-inner SocialDetail-name"><b>{{ Copy }}</b></div>
                <div class="SocialDetail-inner SocialDetail-description">{{ Description }}</div>
            </div>
        </el-button>
        <div v-if="copiedRef" class="copy-success-message">
            <span>内容已复制！</span>
        </div>
    </div>
</template>

<style scoped>
.custom-svg {
    display: block;
    width: 2em !important;
    height: 2em !important;
    object-fit: contain;
}

.main-box .button {
    display: flex;
    justify-content: flex-start;
    padding: 8px;
    width: 35em;
    height: 5em;
}

.SocialIcon {
    height: 4em;
    width: 4em;
    border-radius: 8px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    margin-right: 8px;
    display: flex;
    align-items: center;
    justify-content: center;
}

.SocialDetail {
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    color: rgb(125, 125, 125);
}

.SocialDetail-inner {
    display: flex;
    justify-content: flex-start;
    margin-top: 2px;
    margin-bottom: 2px;
}

.SocialDetail-name {
    font-size: 12px;
}

.SocialDetail-description {
    font-size: 10px;
    color: rgb(192, 192, 192);
}

.el-button {
    border-radius: 8px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.el-button:hover {
    color: #e60012;
}

.copy-success-message {
    position: fixed;
    bottom: 20px;
    left: 50%;
    transform: translateX(-50%);
    background-color: #4caf50;
    color: white;
    padding: 10px 20px;
    border-radius: 5px;
    font-size: 14px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.2);
    opacity: 0; /* 初始设置为不可见 */
    animation: slideInOut 2s ease-in-out forwards;
}

.copy-success-message span {
    display: block;
    text-align: center;
}


@keyframes slideInOut {
    0% {
        bottom: 20px;   /* 初始位置在下方 */
        opacity: 0;      /* 初始不可见 */
    }
    15% {
        bottom: 11em;    /* 顶端偏移，显示出来 */
        opacity: 1;      /* 完全显示 */
    }
    20% {
        bottom: 10em;    /* 顶端偏移，显示出来 */
        opacity: 1;      /* 完全显示 */
    }
    80% {
        bottom: 10em;    /* 保持在显示位置 */
        opacity: 1;      /* 保持可见 */
    }
    100% {
        bottom: 0px;     /* 向上飘出 */
        opacity: 0;      /* 最终消失 */
    }
}

@media screen and (max-width: 768px) {
    .main-box .button {
        width: 70vw;
        height: 5em;
        display: flex;
        justify-content: flex-start;
    }

    .SocialDetail-name {
        font-size: 12px;
    }

    .SocialDetail-description {
        font-size: 12px;
    }
}
</style>
