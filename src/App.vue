<script setup lang="ts">
import Link from './components/Link.vue'
import Avatar from './components/Avatar.vue'
import MyName from './components/MyName.vue'
import Footer from './components/Footer.vue'
import Head from './components/Head.vue'
import ShareButton from './components/ShareButton.vue'
import Email from './components/Email.vue'
import VideoBackground from './components/VideoBackground.vue'
import Copy from './components/Copy.vue'
</script>

<template>
  <ShareButton Msg="司晓龙的 Link Collections" />

  <Head />
  <br>
  <div class="center-container">
    <Avatar Link="https://avatars.githubusercontent.com/u/59590732?v=4" />
    <MyName Name="🌅🐉🔋" />
    <div class="contact">
      <Email Email="email@sixiaolong.win" />
    </div>

    <Link Link="https://sixiaolong.win/" Name="相逢在宇宙 0080" Description="我的个人博客" PlatformsName="Blog"
      Icon="square-rss" IconFamily="fas" />
    <Link Link="https://github.com/SIXiaolong1117" Name="SI Xiaolong" Description="偶尔写点项目~" />
    <Link Link="https://x.com/SI_Xiaolong" Name="司晓龙 | 𝚂𝚒-𝚇𝚒𝚊𝚘 𝚕𝚘𝚘𝚗𝚐" Description="关注技术" />
    <Link Link="https://x.com/SI_Xiaolong_101" Name="司晓龙 | 𝚂𝚒-𝚇𝚒𝚊𝚘 𝚕𝚘𝚘𝚗𝚐 (𝙳𝚊𝚒𝚕𝚢)" Description="我的日常" />
    <Link Link="https://www.instagram.com/si_xiaolong/" Name="si_xiaolong" Description="" />
    <Link Link="https://www.threads.net/@si_xiaolong" Name="SI Xiaolong" Description="不怎么用" />
    <Link Link="https://www.facebook.com/SIXiaolong/" Name="司晓龙" Description="不怎么用" />
    <Link Link="https://www.tiktok.com/@eis0080" Name="Asuka" Description="不怎么用" />
    <Link Link="https://weibo.com/u/7969607960" Name="-Asuka-明日香" Description="不怎么用" />
    <Link Link="https://v.douyin.com/ifU5yQ7K/" Name="Asuka" Description="" />
    <Link Link="https://space.bilibili.com/513864260" Name="拉普拉斯科学计算中心" Description="" />
    <Link Link="zhihu.com/people/eis0080" Name="相逢在宇宙 0080" Description="不怎么用" />
    <Link Link="https://steamcommunity.com/id/Hathaway_UC0105/" Name="Asuka" Description="一起打打游戏不~" />
    <Copy Copy="SW-0486-2360-7135" PlatformsName="Nintendo Switch"
      SvgIcon='<svg xmlns="http://www.w3.org/2000/svg" width="auto" height="auto" viewBox="0 0 448 512"><path d="M95.9 33.5c-44.6 8-80.5 41-91.8 84.4C0 133.6-.3 142.8.2 264.4C.4 376 .5 378.6 2.4 387.3c10.3 46.5 43.3 79.6 90.3 90.5c6.1 1.4 13.9 1.7 64.1 1.9c51.9.4 57.3.3 58.7-1.1c1.4-1.4 1.5-19.3 1.5-222.2c0-150.5-.3-221.3-.9-222.6c-.9-1.7-2.5-1.8-56.9-1.7c-44.2.1-57.5.4-63.3 1.4zm83.9 222.6V444l-37.8-.5c-34.8-.4-38.5-.6-45.5-2.3c-29.9-7.7-52-30.7-58.3-60.7c-2-9.4-2-240.1-.1-249.3c5.6-26.1 23.7-47.7 48-57.4c12.2-4.9 17.9-5.5 57.6-5.6l35.9-.1v188zm-75.9-131.2c-5.8 1.1-14.7 5.6-19.5 9.7c-9.7 8.4-14.6 20.4-13.8 34.5c.4 7.3.8 9.3 3.8 15.2c4.4 9 10.9 15.6 19.9 20c6.2 3.1 7.8 3.4 15.9 3.7c7.3.3 9.9 0 14.8-1.7c20.1-6.8 32.3-26.3 28.8-46.4c-3.9-23.7-26.6-39.7-49.9-35zm158.2-92.3c-.4.3-.6 100.8-.6 223.5c0 202.3.1 222.8 1.5 223.4c2.5.9 74.5.6 83.4-.4c37.7-4.3 71-27.2 89-61.2c2.3-4.4 5.4-11.7 7-16.2c5.8-17.4 5.7-12.8 5.7-146.1c0-106.4-.2-122.3-1.5-129c-9.2-48.3-46.1-84.8-94.5-93.1c-6.5-1.1-16.5-1.4-48.8-1.4c-22.4-.1-40.9.2-41.2.5zm99.1 202.1c14.5 3.8 26.3 14.8 31.2 28.9c3.1 8.7 3 21.5-.1 29.5c-5.7 14.7-16.8 25-31.1 28.8c-23.2 6-47.9-8-54.6-31c-2-7-1.9-18.9.4-26.2c6.9-22.7 31-36.1 54.2-30z" fill="currentColor"/></svg>'
      Description="在等 Switch 2" />
  </div>

  <br>
  <br>
  <br>
  <Footer />
  <VideoBackground />
</template>

<style scoped>
.center-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  min-height: 100vh;
  gap: 20px;
}

.contact {
  display: flex;
  flex-direction: row;
}
</style>
