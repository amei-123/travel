<template>
    <div>
        <router-link tag="div" to="/" class="header-abs" v-show="isShow">
            <div class="iconfont icon-icon07 header-abs-back"></div>
        </router-link>

        <div 
            class="header-fixed" 
            v-show="!isShow"
            :style="opacityStyle"
        >
            <router-link to="/">
                <div class="iconfont header-fixed-back icon-icon07 "></div>
            </router-link>
            景点详情
        </div>
    </div>
</template>

<script>
export default {
    name:'DetailHeader',
    data(){
        return {
            isShow:true,
            opacityStyle:{
                opacity:0
            }
        }
    },
    methods: {
        handleScroll(){
            console.log('scroll');
            const topS = document.documentElement.scrollTop;
            if(topS>60){
                const Opacity = topS/140;
                Opacity>1?1:Opacity;
                this.opacityStyle.opacity = Opacity;
                this.isShow = false;
            }else{
                this.isShow = true;
            }
        }
    },
    mounted() {
        window.addEventListener('scroll',this.handleScroll)
    },
    unmounted(){ //对全局事件的解绑
        window.removeEventListener('scroll')
    }
}
</script>

<style lang="stylus" scoped>
@import '~styles/styles.styl';
    .header-abs
        position: absolute
        left: .2rem
        top: .2rem
        width: .8rem
        height: .8rem
        line-height: .8rem
        border-radius: .4rem
        text-align: center
        background: rgba(0, 0, 0, .8)
        .header-abs-back
            color: #fff
            font-size: .4rem
    .header-fixed
        z-index: 2
        position: fixed
        top: 0
        left: 0
        right: 0
        height: $headerHeight
        line-height: $headerHeight
        text-align: center
        color: #fff
        background: $backgroundColor
        font-size: .32rem
        .header-fixed-back
            position: absolute
            top: 0
            left: 0
            width: .64rem
            text-align: center
            font-size: .4rem
            color: #fff
</style>