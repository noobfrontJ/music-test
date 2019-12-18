<template>
  <div>
    <router-link tag="div" to="/" class="header-abs">
      <span class="iconfont header-abs-back">&#xe624;</span>
    </router-link>
    <div class="header-fixed"></div>
  </div>
</template>

<script>
export default {
  name: 'DetailHeader'
}
</script>

<style lang="stylus" scoped>
.header-abs
    position : absolute
    left : .2rem
    top : .3rem
    width : .8rem
    height : .8rem
    line-height : .8rem
    border-radius : .4rem
    text-align: center;
    background : rgba(0,0,0,.8)
    .header-abs-back
        color : #fff
        font-size : .4rem
</style>
