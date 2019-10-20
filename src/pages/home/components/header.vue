<template>
    <div class="header">
        <div class="header-left"><span class="iconfont icon-icon07"></span></div>
        <div class="header-input"><span class="iconfont icon-sousuo"></span>输入城市/景点/游玩主题</div>
        <router-link to="/city">
            <div class="header-right">{{this.$store.state.city}}<span class="iconfont icon-jiantoudown"></span></div>
        </router-link>
    </div>
</template>

<script>
export default {
    name: 'HomeHeader',
    props:{
        city:String
    },
}
</script>

<style lang="stylus" scoped>
@import '~styles/styles.styl';
    .header
        display: flex
        justify-content :space-between
        line-height: $headerHeight
        background-color: $backgroundColor

        .header-left
            width: 0.64rem
            .icon-icon07
                margin-left: .15rem
                font-size: .55rem
                color:#fff
        .header-input
            flex: 1
            height: .64rem
            margin-top: .12rem
            margin-left: .2rem
            line-height: .64rem
            background-color: #fff
            border-radius: .1rem
            color: #ccc
            .icon-sousuo
                margin: 0 .12rem
        .header-right
            width: 1.24rem
            text-align: center
            color:#fff
            .icon-jiantoudown
                font-size: .2rem

</style>