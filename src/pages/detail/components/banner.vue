<template>
  <div>
    <div class="banner" v-on:click="handleShowClick">
      <img class="banner-img" :src="this.bannerImg" />
      <div class="banner-info">
        <div class="banner-tittle">{{this.sightName}}</div>
        <div class="banner-number">
          <span class="iconfont icon-tupian"></span>
          {{this.bannerImgs.length}}
        </div>
      </div>
    </div>
    <fade-animation>
      <gallary 
        v-bind:imgs="bannerImgs" 
        v-show="showGallary" 
        @handleCloseClick="handleCloseClick"
      >
      </gallary>
    </fade-animation>
  </div>
</template>

<script>
import Gallary from "common/gallary/Gallary";
import FadeAnimation from 'common/fade/FadeAnimation'
export default {
  name: "DetailBanner",
  props: ["sightName", "bannerImg", "bannerImgs"],
  data() {
    return {
      showGallary: false
    };
  },
  components: {
    Gallary,
    FadeAnimation
  },
  methods: {
    handleShowClick() {
      this.showGallary = true;
    },
    handleCloseClick() {
      this.showGallary = false;
    }
  }
};
</script>

<style lang="stylus" scoped>
.banner {
  position: relative;
  overflow: hidden;
  height: 0;
  padding-bottom: 55%;

  .banner-img {
    width: 100%;
  }

  .banner-info {
    display: flex;
    position: absolute;
    left: 0;
    right: 0;
    bottom: 0;
    line-height: 0.6rem;
    color: #fff;
    background-image: linear-gradient(top, rgba(0, 0, 0, 0), rgba(0, 0, 0, 0.8));

    .banner-tittle {
      flex: 1;
      font-size: 0.32rem;
      padding: 0 0.2rem;
    }

    .banner-number {
      height: 0.32rem;
      line-height: 0.32rem;
      margin-top: 0.14rem;
      padding: 0 0.4rem;
      border-radius: 0.2rem;
      background: rgba(0, 0, 0, 0.8);
      font-size: 0.24rem;

      .banner-icon {
        font-size: 0.24rem;
      }
    }
  }
}
</style>