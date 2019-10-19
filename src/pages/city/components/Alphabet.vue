<template>
  <div>
    <ul class="list">
      <li class="item" 
        v-for="key of letters" 
        v-bind:key="key"
        v-on:click="handleClick"
        v-bind:ref="key"
        v-on:touchstart.prevent='handleStart'
        v-on:touchmove='handleMove'
        v-on:touchend='handleEnd'
      >{{key}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "CityAlphabet",
  props: {
    cities: Object
  },
  deta(){
    return{
      isTouch:false,
      topA:0,
      timer:null
    }
  },
  computed:{
    letters(){
      const letterArr = [];
      for(var key in this.cities){
        letterArr.push(key);
      }
      return letterArr;
    }
  },
  updated(){
    this.topA = this.$refs.A[0].offsetTop //加载一次，减少不必要的资源空间
  },
  methods: {
    handleClick(e){
      this.$emit('change',e.target.innerText)
    },
    handleStart(){
      this.isTouch = true;
    },
    handleMove(e){
      if(this.isTouch){
        // this.topA = this.$refs.A[0].offsetTop; 浪费资源性能
        if(this.timer){
          clearTimeout(this.timer)
        }
        this.timer = setInterval(()=>{  //节流 16ms之内执行多次，把上一次的清除，只保留一次
          const topOther = e.touches[0].clientY - 79;
           const index = Math.floor((topOther-this.topA)/20);
          if(index>=0 && index < this.letters.length){
            this.$emit('change',this.letters[index])
          }
        },16)
      }
    },
    handleEnd(){
      this.isTouch = false;
    }
  },
};
</script>

<style lang="stylus" scoped>
@import '~styles/styles.styl';

.list {
  display: flex;
  flex-direction: column;
  justify-content: center;
  position: absolute;
  top: 1.58rem;
  right: 0;
  bottom: 0;
  width: 0.4rem;

  .item {
    line-height: 0.4rem;
    text-align: center;
    color: $backgroundColor;
  }
}
</style>
