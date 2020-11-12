<template>
  <div class = 'page-home'>
    <header class="index-header">
      <a href="mine.html?cpid=0">
        <div class="header-user">
          <div class="user-btn"></div>
        </div>
      </a>
      <div class="header-logo"></div>
      <a href="search.html?cpid=0">
        <div class="header-search"></div>
      </a>
    </header>
    <Swiper :autoplay="2000" :loop="true">
      <Swiper-item>1</Swiper-item>
      <Swiper-item>2</Swiper-item>
      <Swiper-item>3</Swiper-item>
    </Swiper>
  </div>
</template>

<script>

import { Swiper, SwiperItem } from '@/components/Swiper'
import { getbanner } from '@/api/banner'

export default {
  name: 'Home',
  components: {
    Swiper,
    SwiperItem
  },
  methods: {
    changeHandler (payload) {
      console.log('index', payload)
    }
  },
  created () {
    getbanner().then(res => {
      console.log(res)
    })
  }
}

</script>

<style lang='scss' scoped>
@import "@/assets/styles/mixins.scss";
.page-home{
  display: flex;
  flex-direction: column;
  height: 100%;
  .index-header {
    // position: relative;
    // &::after{
    //   content: '';
    //   position: absolute;
    //   width: 100px;
    //   height: 1px;
    //   left: 0px;
    //   bottom: 0px;
    //   background: #ededed;
    //   transform: scaleY(0.5);
    // }
@include border-bottom;
    display: flex;
    height: 44px;
    //三者等分平铺
    justify-content: space-between;
    align-items: center;
    padding: 0 20px;
    box-sizing: border-box;
    .user-btn{
      width: 25px;
      height: 25px;
      background: url(~@/assets/icon/user-btn.png);
      background-size: 100%;
    }
    .header-logo{
      width: 92px;
      height: 28px;
      background: url(~@/assets/logo.png) no-repeat;
      background-size: 100%;
    }
    .header-search{
       width: 25px;
      height: 25px;
      background: url(~@/assets/icon/header-search.png);
      background-size: 100%;
    }
  }
}
</style>
