<template>
  <div>
    <div class="title">热销推荐</div>
    <ul>
      <li
        class="item border-bottom"
        v-for="item of recommendList"
        :key="item.id"
      >
        <div class="item-img-wrapper">
          <img class="item-img" :src="item.imgUrl" />
        </div>
        <div class="item-info">
          <p class="item-title">{{ item.title }}</p>
          <p class="item-desc">{{ item.desc }}</p>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HomeWeekend',
  data() {
    return {
      recommendList: [
        {
          id: '0001',
          imgUrl:
            'https://imgs.qunarzz.com/vs_ceph_vs_tts/249448a3-5bd8-4f0c-bac2-aed51a0d7e00.jpg_r_390x260x90_439fee08.jpg',
          title: '超级测试',
          desc: '测试机器性能'
        },
        {
          id: '0002',
          imgUrl:
            'https://imgs.qunarzz.com/vs_ceph_vs_tts/249448a3-5bd8-4f0c-bac2-aed51a0d7e00.jpg_r_390x260x90_439fee08.jpg',
          title: '大连',
          desc: '大连测试圣地'
        },
        {
          id: '0003',
          imgUrl:
            'https://imgs.qunarzz.com/vs_ceph_vs_tts/249448a3-5bd8-4f0c-bac2-aed51a0d7e00.jpg_r_390x260x90_439fee08.jpg',
          title: '大连',
          desc: '大连测试圣地'
        }
      ]
    }
  }
}
</script>

<style lang="stylus" scoped>
@import '~styles/mixins.styl'
.title
  margin-top : .2rem
  line-height : .8rem
  background : #eee
  text-indent : .2rem
.item-img-wrapper
  overflow : hidden
  height : 0
  padding-bottom : 33.9%
  .item-img
    width : 100%
.item-info
  padding : .1rem
  .item-title
    line-height : .54rem
    font-size : .32rem
    ellipsis()
  .item-desc
    line-height : .4rem
    color : #ccc
    ellipsis()
</style>
