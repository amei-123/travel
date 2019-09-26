<template>
    <div class="header">
        <div class="header-left"><span class="iconfont icon-icon07"></span></div>
        <div class="header-input"><span class="iconfont icon-sousuo"></span>输入城市/景点/游玩主题</div>
        <div class="header-right">城市<span class="iconfont icon-jiantoudown"></span></div>
    </div>
</template>

<script>
export default {
    name: 'HomeHeader'
}
</script>

<style lang="stylus" scoped>
@import '~styles/styles.styl';
    .header
        display: flex
        justify-content :space-between
        line-height: .84rem
        background-color: $backgroundColor

        .header-left
            width: 0.64rem
            .icon-icon07
                margin-left: .15rem
                font-size: .55rem
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
            .icon-jiantoudown
                font-size: .2rem

</style>