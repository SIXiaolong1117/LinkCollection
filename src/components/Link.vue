<script setup lang="ts">
import { computed } from 'vue';

const { Link, Name, PlatformsName, Description, Icon, IconFamily, SvgIcon } = defineProps<{
    Link: string;
    Name: string;
    PlatformsName?: string;
    Description?: string;
    Icon?: string;
    IconFamily?: string;
    SvgIcon?: string;
}>();

// 解析输入链接
const SocialPlatforms = computed(() => {
    const platform = {
        platformsName: 'Unknown',
        iconfamily: 'fas',
        icon: 'square-full',
        isCustomSvgIcon: false
    };

    if (Link.includes('github.com')) {
        platform.platformsName = 'GitHub';
        platform.iconfamily = 'fab';
        platform.icon = 'square-github';
    } else if (Link.includes('x.com')) {
        platform.platformsName = 'X';
        platform.iconfamily = 'fab';
        platform.icon = 'square-x-twitter';
    } else if (Link.includes('twitter.com')) {
        platform.platformsName = 'Twitter';
        platform.iconfamily = 'fab';
        platform.icon = 'x-twitter';
    } else if (Link.includes('bilibili.com')) {
        platform.platformsName = 'BiliBili';
        platform.iconfamily = 'fab';
        platform.icon = 'bilibili';
    } else if (Link.includes('instagram.com')) {
        platform.platformsName = 'Instagram';
        platform.iconfamily = 'fab';
        platform.icon = 'square-instagram';
    } else if (Link.includes('threads.net')) {
        platform.platformsName = 'Threads';
        platform.iconfamily = 'fab';
        platform.icon = 'square-threads';
    } else if (Link.includes('weibo.com')) {
        platform.platformsName = 'Weibo';
        platform.iconfamily = 'fab';
        platform.icon = 'weibo';
    } else if (Link.includes('steamcommunity.com')) {
        platform.platformsName = 'Steam';
        platform.iconfamily = 'fab';
        platform.icon = 'square-steam';
    } else if (Link.includes('facebook.com')) {
        platform.platformsName = 'Facebook';
        platform.iconfamily = 'fab';
        platform.icon = 'square-facebook';
    } else if (Link.includes('douyin.com') || Link.includes('tiktok.com')) {
        if (Link.includes('douyin.com')) {
            platform.platformsName = 'Douyin';
        } else if (Link.includes('tiktok.com')) {
            platform.platformsName = 'Tiktok';
        }
        platform.iconfamily = 'fab';
        platform.icon = 'tiktok';
    }

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

const openLink = () => {
    window.open(Link, '_blank');
};
</script>

<template>
    <div class="main-box">
        <el-button class="button" plain @click="openLink">
            <div class="SocialIcon">
                <template v-if="SocialPlatforms.isCustomSvgIcon">
                    <div class="custom-svg" v-html="SocialPlatforms.icon"></div>
                </template>
                <template v-else>
                    <font-awesome-icon :icon="[SocialPlatforms.iconfamily, SocialPlatforms.icon]" size="2x" />
                </template>
            </div>
            <div class="SocialDetail">
                <div class="SocialDetail-inner"><b>{{ SocialPlatforms.platformsName }}</b></div>
                <div class="SocialDetail-inner SocialDetail-name"><b>{{ Name }}</b></div>
                <div class="SocialDetail-inner SocialDetail-description">{{ Description }}</div>
            </div>
        </el-button>
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
    font-size: 14px;
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
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.2);
}

.el-button:hover {
    color: #e60012;
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