<template>
  <div class="img-container">
    <swiper :options="swiperOption" >
      <swiper-slide v-for="item in imgArr" :key="item.id">
        <img :src="item.url" class="swiper-img">
      </swiper-slide>
      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
export default {
    name:'HomeSwiper',
    data() {
      return {
        swiperOption: {
            pagination:'.swiper-pagination',
            loop:true,
            // cancelable:true
        },
        imgArr:[
          {
            id:'001',
            url:'https://img1.qunarzz.com/order/comp/1805/2e/6e407f088bfb902.png'
          },
          {
            id:'002',
            url:'https://img1.qunarzz.com/order/comp/1805/2e/6e407f088bfb902.png'
          },
          {
            id:'003',
            url:"https://img1.qunarzz.com/order/comp/1805/2e/6e407f088bfb902.png"
          }
        ]
      }
    },
}
</script>

<style lang="stylus" scoped>
  .img-container >>> .swiper-pagination-bullet-active 
    background-color :$backgroundColor !important;
  .img-container{
    overflow :hidden;
    width :100%;
    height :0;
    padding-bottom :40%;
    .swiper-img{
      width :100%;
      height :100%;
    }
  }
</style>