<template>
    <swiper >
        <swiper-slide v-for="(item,index) in pages" :key="index" class="icon-container">
            <div class="icon-item" v-for="img in item" :key="img.id">
                <img src="https://s.qunarzz.com/vacation_react/around/entry5.png" class="icon-img">
                <p class="icon-detail">{{img.detail}}</p>
            </div>
        </swiper-slide>
    </swiper>
</template>

<script>
export default {
    name:'HomeIcons',
    data(){
        return{
            iconArr:[
                {id:'001',url:'https://s.qunarzz.com/vacation_react/around/entry5.png',detail:'游遍全球游遍全球'},
                {id:'002',url:'https://s.qunarzz.com/vacation_react/around/entry5.png',detail:'游遍全球'},
                {id:'003',url:'https://s.qunarzz.com/vacation_react/around/entry5.png',detail:'游遍全球'},
                {id:'004',url:'https://s.qunarzz.com/vacation_react/around/entry5.png',detail:'游遍全球'},
                {id:'005',url:'https://s.qunarzz.com/vacation_react/around/entry5.png',detail:'游遍全球'},
                {id:'006',url:'https://s.qunarzz.com/vacation_react/around/entry5.png',detail:'游遍全球'},
                {id:'007',url:'https://s.qunarzz.com/vacation_react/around/entry5.png',detail:'游遍全球'},
                {id:'008',url:'https://s.qunarzz.com/vacation_react/around/entry5.png',detail:'游遍全球'},
                {id:'009',url:'https://s.qunarzz.com/vacation_react/around/entry5.png',detail:'游遍全球'}
            ]
        }
    },
    computed: {
        pages () {  //分页实现轮播
            let pages = [];
            this.iconArr.forEach((item,index)=>{
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
            .icon-detail
                font-size:12px;
                color:$textColor;
                overflow :hidden;
                text-overflow :ellipsis;
                white-space :nowrap;
</style>