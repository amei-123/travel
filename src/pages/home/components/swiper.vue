<template>
  <div class="img-container">
    <swiper :options="swiperOption" v-if="getListLength">
      <swiper-slide v-for="item in swiperList" :key="item.id">
        <img :src="item.imgUrl" class="swiper-img">
      </swiper-slide>
      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
export default {
    name:'HomeSwiper',
    props:{
      swiperList:Array
    },
    data() {
      return {
        swiperOption: {
            pagination:'.swiper-pagination',
            loop:true,
            // cancelable:true
        }
      }
    },
    computed:{
      getListLength(){
        return this.swiperList.length;
      }
    }
}
</script>

<style lang="stylus" scoped>
  .img-container >>> .swiper-pagination-bullet-active 
    background-color :$backgroundColor !important;
  .img-container{
    overflow :hidden;
    width :100%;
    height :0;
    padding-bottom :32%;
    .swiper-img{
      width :100%;
      height :100%;
    }
  }
</style>