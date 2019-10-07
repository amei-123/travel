<template>
    <div>
        <div class="title">热门推荐</div>
        <ul> 
            <li  class="itemList" v-for="item in itemArr" :key="item.id">
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
    data(){
        return{
            itemArr:[
                {
                id:'0001',
                imgUrl:'https://s.qunarzz.com/vacation_react/around/entry5.png',
                title:'迪士尼游乐园',
                desc:'开放了开放了,全场打五折'
                }
                ,{
                    id:'0002',
                    imgUrl:'https://s.qunarzz.com/vacation_react/around/entry5.png',
                    title:'迪士尼游乐园',
                    desc:'开放了开放了,全场打五折'
                }
                ,{
                    id:'0003',
                    imgUrl:'https://s.qunarzz.com/vacation_react/around/entry5.png',
                    title:'迪士尼游乐园',
                    desc:'开放了开放了,全场打五折'
                }
            ]
        }
    }
}
</script>

<style lang="stylus" scoped>
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
                .item-title
                    line-height :.54rem;
                    font-size :.32rem;
                .item-desc
                    line-height:.4rem;
                    color :#333;
                .item-info
                    margin-top:.1rem;
                    line-height :.44rem;
                    background-color :#888;
                    border-radius :.05rem;
</style>