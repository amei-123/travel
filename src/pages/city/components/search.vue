<template>
    <div>
        <div class="search">
            <input v-model='keyWord' class="search-input" type="text" placeholder="输入城市名或拼音" />
        </div>
        <div class="search-content" v-show="keyWord">
            <ul class="search-item border-bottom">
                <li v-for="item of list" :key="item.id">{{item.name}}</li>
                <li v-show="!list.length">未查找到匹配数据!</li>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
  name: 'CitySearch',
  data(){
      return{
          keyWord:'',
          timer: null,
        list:[]
      }
  },
  props:{
      cities:Object
  },
  watch:{
      keyWord(){
       const result = [];
        if (this.timer) { //限流
            clearTimeout(this.timer)
        }
        if(!this.keyWord){
            this.list = [];
        }
        this.timer = setTimeout(() => {
            const result = []
            for (let i in this.cities) {
                this.cities[i].forEach((value) => {
                    if (value.spell.indexOf(this.keyWord) > -1 || value.name.indexOf(this.keyWord) > -1) {
                       result.push(value)
                    }
                })
            }
            this.list = result
      }, 100)
    }
  }
}
</script>

<style lang="stylus" scoped>
@import '~styles/styles.styl';
    .search
        height: .72rem
        padding: 0 .1rem
        background: $backgroundColor
        .search-input
            box-sizing: border-box
            width: 100%
            height: .62rem
            padding: 0 .1rem
            line-height: .62rem
            text-align: center
            border-radius: .06rem
            color: #666
    .search-content
        z-index: 1
        overflow: hidden
        position: absolute
        top: 1.58rem
        left: 0
        right: 0
        bottom: 0
        background: #eee
        .search-item
            line-height: .62rem
            padding-left: .2rem
            background: #fff
            color: #666
</style>