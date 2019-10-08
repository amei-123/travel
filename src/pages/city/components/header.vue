<template>
    <div class='header'>
        城市选择
        <router-link to="/">
            <div class="iconfont icon-icon07 header-back"></div>
        </router-link>
    </div>
</template>

<script>
export default {
  name: 'CityHeader'
}
</script>

<style lang="stylus" scoped>
@import '~styles/styles.styl';
    .header
        position: relative
        overflow: hidden
        height: $headerHeight
        line-height: $headerHeight
        text-align: center
        color: #fff
        background: $backgroundColor
        font-size: .32rem
        .header-back
            position: absolute
            top: 0
            left: 0
            width: .64rem
            text-align: center
            font-size: .4rem
            color: #fff
</style>