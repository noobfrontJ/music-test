<template>
  <div id="app">
    <!-- <img src="./assets/logo.png"> -->
    <m-header></m-header>
    <tab></tab>
    <router-view />
  </div>
</template>

<script type="text/ecmascript-6">
import MHeader from 'components/m-header/m-header'
import Tab from 'components/tab/tab'
export default {
  components: {
    MHeader,
    Tab
  }
}
</script>

<style lang="stylus" scoped rel="stylesheet/stylus">
@import './common/stylus/variable'

#app {
  color: $color-theme
}
</style>
