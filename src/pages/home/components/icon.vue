<template>
    <swiper  :options="swiperOption">
        <swiper-slide v-for="(item,index) in pages" :key="index" class="icon-container">
            <div class="icon-item" v-for="img in item" :key="img.id">
                <img :src="img.imgUrl" class="icon-img">
                <p class="icon-desc">{{img.desc}}</p>
            </div>
        </swiper-slide>
    </swiper>
</template>

<script>
export default {
    name:'HomeIcons',
    props:{
        iconList:Array
    },
    data(){
        return{
            swiperOption: {
                autoplay:false
            }
        }
    },
    computed: {
        pages () {  //分页实现轮播
            let pages = [];
            this.iconList.forEach((item,index)=>{
                var p = Math.floor(index/8);
                if(!pages[p]){
                    pages[p] = [];
                }
                pages[p].push(item);
            })
            return pages;
        }
    },
}
</script>

<style lang="stylus" scoped>
    @import '~styles/styles.styl'
    @import '~styles/ellipsis.styl'
    .icon-container
        overflow :hidden;
        display :flex;
        flex-wrap :wrap;
        justify-content :space-between;
        width :100%;
        
        .icon-item
            display :flex;
            justify-content :center;
            align-items:center;
            flex-wrap :wrap;
            width :25%;
            box-sizing :border-box;
            padding:0 10px;
            .icon-img
                width:1.2rem;
                height:1.2rem
            .icon-desc
                font-size:12px;
                color:$textColor;
                ellipsis();
</style>