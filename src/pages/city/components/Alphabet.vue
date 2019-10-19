<template>
  <div>
    <ul class="list">
      <li class="item" v-for="(item,key) of cities" v-bind:key="key">{{key}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "CityAlphabet",
  props: {
    cities: Object
  }
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
