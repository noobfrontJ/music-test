<template>
  <div class="wrapper">
    <swiper :options="swiperOption">
      <!-- slides -->
      <swiper-slide v-for="item of swiperList" :key="item">
        <img class="swiper-img" :src="item.imgUrl" />
      </swiper-slide>
      <!-- optional -->
      <div class="swiper-pagination" slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
export default {
  name: 'HomeSwiper',
  data() {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        loop: true
      },
      swiperList: [
        {
          id: '0001',
          imgUrl:
            'https://imgs.qunarzz.com/vs_ceph_vs_tts/249448a3-5bd8-4f0c-bac2-aed51a0d7e00.jpg_r_390x260x90_439fee08.jpg'
        },
        {
          id: '0002',
          imgUrl:
            'https://imgs.qunarzz.com/p/tts7/1612/b3/d43918d716d51d02.jpg_r_390x260x90_8f1d8855.jpg'
        }
      ]
    }
  }
}
</script>

<style lang="stylus" scoped>
.wrapper >>> .swiper-pagination-bullet-active
    background : #fff !important
.wrapper
    overflow : hidden
    width : 100%
    height : 0
    padding-bottom : 67.25%
    background : #eee
    .swiper-img
        width : 100%
</style>
