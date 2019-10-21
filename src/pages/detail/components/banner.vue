<template>
  <div>
    <div class="banner" v-on:click="handleShowClick">
      <img class="banner-img" src="https://imgs.qunarzz.com/p/tts0/1811/2b/8cc21c8160981f02.jpg_r_390x260x90_819c3305.jpg" />
      <div class="banner-info">
        <div class="banner-tittle">哈哈哈哈哈</div>
        <div class="banner-number">
          <span class="iconfont icon-tupian"></span>
          49
        </div>
      </div>
    </div>
    <gallary 
        v-bind:imgs="imgs" 
        v-show="showGallary"
        @handleCloseClick='handleCloseClick'
    ></gallary>
  </div>
</template>

<script>
import Gallary from 'common/gallary/Gallary'
export default {
  name: "DetailBanner",
  data(){
      return{
          imgs:[
              "https://imgs.qunarzz.com/p/tts0/1811/2b/8cc21c8160981f02.jpg_r_390x260x90_819c3305.jpg",
              "https://imgs.qunarzz.com/p/tts2/1711/d5/0e0ebe3437863d02.jpg_r_480x320x90_e8bdc303.jpg"
          ],
          showGallary:false
      }
  },
  components:{
      Gallary
  },
  methods: {
      handleShowClick(){
          this.showGallary = true;
      },
      handleCloseClick(){
          this.showGallary = false;
      }
  },
};
</script>

<style lang="stylus" scoped>
    .banner
        position: relative
        overflow: hidden
        height: 0
        padding-bottom: 55%
        .banner-img
            width: 100%
        .banner-info
            display: flex
            position: absolute
            left: 0
            right: 0
            bottom: 0
            line-height: .6rem
            color: #fff
            background-image: linear-gradient(top, rgba(0, 0, 0, 0), rgba(0, 0, 0, 0.8))
            .banner-tittle
                flex: 1
                font-size: .32rem
                padding: 0 .2rem
            .banner-number
                height: .32rem
                line-height: .32rem
                margin-top: .14rem
                padding: 0 .4rem
                border-radius: .2rem
                background: rgba(0, 0, 0, .8)
                font-size: .24rem
                .banner-icon
                    font-size: .24rem
</style>