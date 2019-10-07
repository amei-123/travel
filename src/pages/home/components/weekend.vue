<template>
  <div>
    <div class="title">周末去哪儿</div>
    <ul>
      <li
        class="item border-bottom"
        v-for="item in itemArr"
        :key="item.id"
      >
        <div class="item-img-wrapper">
          <img class="item-img" :src="item.imgUrl" />
        </div>
        <div class="item-info">
          <p class="item-title">{{item.title}}</p>
          <p class="item-desc">{{item.desc}}</p>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HomeWeekend',
  data(){
        return{
            itemArr:[
                {
                id:'0001',
                imgUrl:'https://img1.qunarzz.com/vc/a9/4e/39/331ab7c6229574d449ab097fb8.jpg_650x360x92.jpg',
                title:'迪士尼游乐园',
                desc:'开放了开放了,全场打五折开放了开放了,全场打五折'
                }
                ,{
                    id:'0002',
                    imgUrl:'https://img1.qunarzz.com/vc/a9/4e/39/331ab7c6229574d449ab097fb8.jpg_650x360x92.jpg',
                    title:'迪士尼游乐园',
                    desc:'开放了开放了,全场打五折'
                }
                ,{
                    id:'0003',
                    imgUrl:'https://img1.qunarzz.com/vc/a9/4e/39/331ab7c6229574d449ab097fb8.jpg_650x360x92.jpg',
                    title:'迪士尼游乐园',
                    desc:'开放了开放了,全场打五折'
                }
            ]
        }
    }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/ellipsis.styl'
  .title
    line-height: .8rem
    background: #eee
    text-indent: .2rem
  .item-img-wrapper
    overflow: hidden
    height: 0
    padding-bottom: 37.09%
    .item-img
      width: 100%
  .item-info
    padding: .1rem
    .item-title
      line-height: .54rem
      font-size: .32rem
      ellipsis()
    .item-desc
      line-height: .4rem
      color: #ccc
      ellipsis()
</style>
