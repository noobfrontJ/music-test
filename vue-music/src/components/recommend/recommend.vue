<template>
  <div class="recommend">
    <div class="recommend-content">
      <div v-if="recommends.length" class="slider-wrapper">
          <slider>
            <div v-for="item in recommends" v-bind:key="item">
              <a :href="item.linkUrl">
                <img :src="item.picUrl" />
              </a>
            </div>
          </slider>
        </div>
        <div class="recommend-list">
          <h1 class="list-title">热门歌单推荐</h1>
          <!-- <ul>
            <li
              @click="selectItem(item)"
              v-for="item in discList"
              v-bind:key="item"
              class="item"
            >
              <div class="icon">
                <img width="60" height="60" v-lazy="item.imgurl" />
              </div>
              <div class="text">
                <h2 class="name" v-html="item.creator.name"></h2>
                <p class="desc" v-html="item.dissname"></p>
              </div>
            </li>
          </ul> -->
      </div>
      <!-- <div class="loading-container" v-show="!discList.length">
        <loading></loading>
      </div> -->
      <!-- </scroll> -->
    </div>
    <!-- <router-view></router-view> -->
  </div>
</template>

<script type="text/ecmascript-6">
import Slider from 'base/slider/slider'
import Scroll from 'base/scroll/scroll'
import {getRecommend} from 'api/recommend'
import {ERR_OK} from 'api/config'

export default{
  data () {
    return {
      recommends: []
    }
  },
  created () {
    this._getRecommend()
  },
  methods: {
    _getRecommend () {
      getRecommend().then((res) => {
        if (res.code === ERR_OK) {
          this.recommends = res.data.slider
        }
      })
      if (this.recommends.length === 0) {
        let _json = '{"code":0,"data":{"slider":[{"linkUrl":"https://github.com/noobfrontJ/music-test","picUrl":"https://camo.githubusercontent.com/0507272050d2be2ba859459c095cf78b96132d6d/68747470733a2f2f302e67726176617461722e636f6d2f6176617461722f31383963633738643962326331356338626261656662323765373535643136663f643d68747470732533412532462532466769746875622e6769746875626173736574732e636f6d253246696d6167657325324667726176617461727325324667726176617461722d757365722d3432302e706e6726723d6726733d3430"},{"linkUrl":"https://github.com/noobfrontJ/music-test","picUrl":"https://camo.githubusercontent.com/0507272050d2be2ba859459c095cf78b96132d6d/68747470733a2f2f302e67726176617461722e636f6d2f6176617461722f31383963633738643962326331356338626261656662323765373535643136663f643d68747470732533412532462532466769746875622e6769746875626173736574732e636f6d253246696d6167657325324667726176617461727325324667726176617461722d757365722d3432302e706e6726723d6726733d3430"},{"linkUrl":"https://github.com/noobfrontJ/music-test","picUrl":"https://camo.githubusercontent.com/0507272050d2be2ba859459c095cf78b96132d6d/68747470733a2f2f302e67726176617461722e636f6d2f6176617461722f31383963633738643962326331356338626261656662323765373535643136663f643d68747470732533412532462532466769746875622e6769746875626173736574732e636f6d253246696d6167657325324667726176617461727325324667726176617461722d757365722d3432302e706e6726723d6726733d3430"},{"linkUrl":"https://github.com/noobfrontJ/music-test","picUrl":"https://camo.githubusercontent.com/0507272050d2be2ba859459c095cf78b96132d6d/68747470733a2f2f302e67726176617461722e636f6d2f6176617461722f31383963633738643962326331356338626261656662323765373535643136663f643d68747470732533412532462532466769746875622e6769746875626173736574732e636f6d253246696d6167657325324667726176617461727325324667726176617461722d757365722d3432302e706e6726723d6726733d3430"}]}}'
        this.recommends = JSON.parse(_json).data.slider
      }
    }
  },
  components: {
    Slider,
    Scroll
  }
}
// import Slider from 'base/slider/slider'
// import Loading from 'base/loading/loading'
// import Scroll from 'base/scroll/scroll'
// import {getRecommend, getDiscList} from 'api/recommend'
// import {playlistMixin} from 'common/js/mixin'
// import {ERR_OK} from 'api/config'
// import {mapMutations} from 'vuex'

// export default {
//   mixins: [playlistMixin],
//   data() {
//     return {
//       recommends: [],
//       discList: []
//     }
//   },
//   created() {
//     this._getRecommend()

//     this._getDiscList()
//   },
//   methods: {
//     handlePlaylist(playlist) {
//       const bottom = playlist.length > 0 ? '60px' : ''

//       this.$refs.recommend.style.bottom = bottom
//       this.$refs.scroll.refresh()
//     },
//     loadImage() {
//       if (!this.checkloaded) {
//         this.checkloaded = true
//         this.$refs.scroll.refresh()
//       }
//     },
//     selectItem(item) {
//       this.$router.push({
//         path: `/recommend/${item.dissid}`
//       })
//       this.setDisc(item)
//     },
//     _getRecommend() {
//       getRecommend().then((res) => {
//         if (res.code === ERR_OK) {
//           this.recommends = res.data.slider
//         }
//       })
//     },
//     _getDiscList() {
//       getDiscList().then((res) => {
//         if (res.code === ERR_OK) {
//           this.discList = res.data.list
//         }
//       })
//     },
//     ...mapMutations({
//       setDisc: 'SET_DISC'
//     })
//   },
//   components: {
//     Slider,
//     Loading,
//     Scroll
//   }
// }
//
</script>

<style scoped lang="stylus" rel="stylesheet/stylus">
@import "~common/stylus/variable"

.recommend
  position: fixed
  width: 100%
  top: 88px
  bottom: 0
  .recommend-content
    height: 100%
    overflow: hidden
    .slider-wrapper
      position: relative
      width: 100%
      overflow: hidden
    .recommend-list
      .list-title
        height: 65px
        line-height: 65px
        text-align: center
        font-size: $font-size-medium
        color: $color-theme
      .item
        display: flex
        box-sizing: border-box
        align-items: center
        padding: 0 20px 20px 20px
        .icon
          flex: 0 0 60px
          width: 60px
          padding-right: 20px
        .text
          display: flex
          flex-direction: column
          justify-content: center
          flex: 1
          line-height: 20px
          overflow: hidden
          font-size: $font-size-medium
          .name
            margin-bottom: 10px
            color: $color-text
          .desc
            color: $color-text-d
    .loading-container
      position: absolute
      width: 100%
      top: 50%
      transform: translateY(-50%)
</style>
