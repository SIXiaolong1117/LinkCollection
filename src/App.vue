<script setup lang="ts">
import Link from './components/Link.vue'
import Avatar from './components/Avatar.vue'
import MyName from './components/MyName.vue'
import Footer from './components/Footer.vue'
import Head from './components/Head.vue'
import ShareButton from './components/ShareButton.vue'
import Email from './components/Email.vue'
</script>

<template>
  <video class="video-background" autoplay loop muted playsinline>
    <source
      src="https://cdn.fastly.steamstatic.com/steamcommunity/public/images/items/2861720/85882f90ad8ca69467610883a9fa95ecc2f071ab.webm"
      type="video/webm" />
    Your browser does not support the video tag.
  </video>


  <ShareButton Msg="司晓龙的 Link Collections" />

  <Head />
  <br>
  <div class="center-container">
    <Avatar Link="https://avatars.githubusercontent.com/u/59590732?v=4" />
    <MyName Name="🌅🐉🔋" />
    <Email Email="email@sixiaolong.win" />

    <Link Link="https://myblog.sixiaolong.win/" Name="相逢在宇宙 0080" Description="我的个人博客" PlatformsName="Blog"
      Icon="square-rss" IconFamily="fas" />
    <Link Link="https://github.com/SIXiaolong1117" Name="SI Xiaolong" Description="偶尔写点项目~" />
    <Link Link="https://x.com/SI_Xiaolong" Name="司晓龙 | 𝚂𝚒-𝚇𝚒𝚊𝚘 𝚕𝚘𝚘𝚗𝚐" Description="关注技术" />
    <Link Link="https://x.com/SI_Xiaolong_101" Name="司晓龙 | 𝚂𝚒-𝚇𝚒𝚊𝚘 𝚕𝚘𝚘𝚗𝚐 (𝙳𝚊𝚒𝚕𝚢)" Description="我的日常" />
    <Link Link="https://space.bilibili.com/513864260" Name="拉普拉斯科学计算中心" Description="" />
    <Link Link="https://www.instagram.com/si_xiaolong/" Name="si_xiaolong" Description="" />
    <Link Link="https://www.threads.net/@si_xiaolong" Name="SI Xiaolong" Description="" />
    <Link Link="https://www.facebook.com/SIXiaolong/" Name="司晓龙" Description="" />
    <Link Link="https://www.tiktok.com/@eis0080" Name="Asuka" Description="不怎么用" />
    <Link Link="https://weibo.com/u/7969607960" Name="-Asuka-明日香" Description="不怎么用" />
    <Link Link="https://v.douyin.com/ifU5yQ7K/" Name="Asuka" Description="" />
    <Link Link="https://steamcommunity.com/id/Hathaway_UC0105/" Name="Asuka" Description="一起打打游戏不~" />
  </div>

  <br>
  <br>
  <br>
  <Footer />
</template>

<style scoped>
.center-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  min-height: 100vh;
  gap: 20px;
}

.video-background {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  z-index: -1;
  opacity: 0.2;
}
</style>
