<script setup lang="ts">
import { ref } from 'vue';
import QRCode from 'qrcode';

const props = defineProps<{ Msg: string }>();
const showQRCodeDialog = ref(false);
const qrCodeDataUrl = ref<string>('');
const currentUrl = window.location.href; // 当前页面链接

// 生成二维码
function generateQRCode() {
    QRCode.toDataURL(currentUrl, { width: 200 })
        .then((url) => {
            console.log('二维码生成成功:', url); // 调试用
            qrCodeDataUrl.value = url; // 设置二维码图片数据
            showQRCodeDialog.value = true; // 显示弹窗
        })
        .catch((error) => {
            console.error('二维码生成失败:', error); // 调试用
        });
}

// 分享页面链接
function sharePageLink() {
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

// 复制链接
const copiedRef = ref(false);
function copyLink() {
    navigator.clipboard.writeText(currentUrl).then(() => {
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
    <el-button circle class="floating-share-button" @click="generateQRCode">
        <font-awesome-icon :icon="['fas', 'share-from-square']" size="2x" class="share-icon" />
    </el-button>

    <el-dialog v-model="showQRCodeDialog" width="25em" :close-on-click-modal="false" :destroy-on-close="true">
        <div class="qrcode-container">
            <div class="qrcode-container-text"><b>𝓛𝓲𝓷𝓴 𝓒𝓸𝓵𝓵𝓮𝓬𝓽𝓲𝓸𝓷</b></div>
            <img class="qrcode-img" v-if="qrCodeDataUrl" :src="qrCodeDataUrl" alt="QR Code" />
            <el-button link class="copy-link" @click="copyLink">
                <div class="copy-link-text">
                    <div class="copy-link-text-link">
                        {{ currentUrl }}
                    </div>
                    <div class="copy-link-text-copy"><font-awesome-icon :icon="['fas', 'copy']" />&nbsp;复制链接
                    </div>
                </div>
            </el-button>
            <el-button class="share-button" @click="sharePageLink">
                <font-awesome-icon :icon="['fas', 'share']" />
                <div class="share-button-text"><b>&nbsp;分享</b></div>
            </el-button>
        </div>
    </el-dialog>

    <div v-if="copiedRef" class="copy-success-message">
        <span>内容已复制！</span>
    </div>
</template>

<style scoped>
.share-button {
    margin-top: 2em;
    width: 15em;
    height: 3em;
    background-color: rgb(45, 45, 45);
    color: rgb(255, 255, 255);
}

.share-button-text{
    font-size: 1.2em;
}

.share-button:hover {
    background-color: rgba(30, 30, 30) !important;
    color: rgb(255, 255, 255);
}

.copy-link {
    width: 15em;
    margin-top: .2em;
}

.copy-link-text {
    width: 15em;
    overflow-wrap: break-word;
    font-size: 1em;
    color: black;
}

.copy-link-text-copy {
    margin-top: .5em;
}

.qrcode-container {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding: 20px 0;
}

.qrcode-container-text {
    font-size: 1.8em;
    color: black;
}

.qrcode-img {
    width: 15em;
    border: 1px solid rgba(0, 0, 0, 0.5);
}

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
    opacity: 0;
    /* 初始设置为不可见 */
    animation: slideInOut 2s ease-in-out forwards;
}

.copy-success-message span {
    display: block;
    text-align: center;
}


@keyframes slideInOut {
    0% {
        bottom: 20px;
        /* 初始位置在下方 */
        opacity: 0;
        /* 初始不可见 */
    }

    15% {
        bottom: 11em;
        /* 顶端偏移，显示出来 */
        opacity: 1;
        /* 完全显示 */
    }

    20% {
        bottom: 10em;
        /* 顶端偏移，显示出来 */
        opacity: 1;
        /* 完全显示 */
    }

    80% {
        bottom: 10em;
        /* 保持在显示位置 */
        opacity: 1;
        /* 保持可见 */
    }

    100% {
        bottom: 0px;
        /* 向上飘出 */
        opacity: 0;
        /* 最终消失 */
    }
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
