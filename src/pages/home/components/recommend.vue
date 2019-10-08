<template>
    <div>
        <div class="title">热门推荐</div>
        <ul> 
            <li  class="itemList" v-for="item in recommendList" :key="item.id">
                <img :src="item.imgUrl" class="item-img">
                <div class="item-conetent">
                    <p class="item-title">{{item.title}}</p>
                    <p class="item-desc">{{item.desc}}</p>
                    <button class="item-info">查看详情</button>
                </div>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    name:'HomeRecommend',
    props:{
        recommendList:Array
    },
    data(){
        return{
        
        }
    }
}
</script>

<style lang="stylus" scoped>
    @import '~styles/ellipsis.styl'
    .title
        width :100%;
        margin-top:.2rem;
        line-height :.8rem;
        font-size:.4rem;
        background-color :#eee;
    ul
        .itemList
            display :flex;
            height :1.9rem;
            border-bottom :1px solid #efefef;
            .item-img
                width :1.7rem;
                height :1.7rem;
                padding :.1rem;
            .item-conetent
                flex :1;
                min-width :0;
                .item-title
                    line-height :.54rem;
                    font-size :.32rem;
                    color :#000;
                    ellipsis();
                .item-desc
                    line-height:.4rem;
                    color :#333;
                    ellipsis();
                .item-info
                    margin-top:.1rem;
                    line-height :.44rem;
                    background-color :#888;
                    border-radius :.05rem;
                    
</style>