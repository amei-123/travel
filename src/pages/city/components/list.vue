<template>
  <div class="list" ref="wrapper">
    <div>
      <div class="area">
        <div class="title border-topbottom">当前城市</div>
        <div class="button-list">
          <div class="button-wrapper">
            <div class="button">{{this.$store.state.city}}</div>
          </div>
        </div>
      </div>
      <div class="area">
        <div class="title border-topbottom">热门城市</div>
        <div class="button-list">
          <div 
            class="button-wrapper" 
            v-for="item of hot" 
            v-bind:key="item.id"
            v-on:click="handleClick(item.name)"
          >
            <div class="button">{{item.name}}</div>
          </div>
        </div>
      </div>
      <div class="area" 
        v-for="(item,key) of cities" 
        v-bind:key="key"
        v-bind:ref="key"
    >
        <div class="title border-topbottom">{{key}}</div>
        <div 
          class="item-list" 
          v-for="city in item" 
          :key="city.id"
          v-on:click="handleClick(city.name)"
        >
          <div class="item border-bottom">{{city.name}}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Bscroll from "better-scroll";
export default {
  name: "CityList",
  props: {
    hot: Array,
    cities: Object,
    letter : String
  },
  methods: {
    handleClick(city){
      this.$store.commit('changeCity',city);
      this.$router.push('/');
    }
  },
  mounted() {
    this.scroll = new Bscroll(this.$refs.wrapper, {
      mouseWheel: true
    });
  },
  watch:{
    letter(){
        if(this.letter){
            const element = this.$refs[this.letter][0];
            this.scroll.scrollToElement(element);//点击相应的字母显示相应的城市区域
        }
    }
  }
};
</script>

<style lang="stylus" scoped>
.border-topbottom {
  &:before {
    border-color: #ccc;
  }

  &:after {
    border-color: #ccc;
  }
}

.border-bottom {
  &:before {
    border-color: #ccc;
  }
}

.list {
  overflow: hidden;
  position: absolute;
  top: 1.58rem;
  left: 0;
  right: 0;
  bottom: 0;
}

.title {
  line-height: 0.54rem;
  background: #eee;
  padding-left: 0.2rem;
  color: #666;
  font-size: 0.26rem;
}

.button-list {
  overflow: hidden;
  padding: 0.1rem 0.6rem 0.1rem 0.1rem;

  .button-wrapper {
    float: left;
    width: 33.33%;

    .button {
      margin: 0.1rem;
      padding: 0.1rem 0;
      text-align: center;
      border: 0.02rem solid #ccc;
      border-radius: 0.06rem;
    }
  }
}

.item-list {
  .item {
    line-height: 0.76rem;
    padding-left: 0.2rem;
  }
}
</style>