<template>
    <div>
        <city-header></city-header>
        <city-search v-bind:cities="cities"></city-search>
        <city-list 
            v-bind:cities='cities' 
            v-bind:hot="hotCities"
            v-bind:letter="letter"
        ></city-list>
        <city-alphabet 
            v-bind:cities='cities'
            v-on:change='handleLetter'
        ></city-alphabet>
    </div>
</template>

<script>
import CityHeader from './components/header'
import CitySearch from './components/search'
import CityList from './components/list'
import CityAlphabet from './components/Alphabet'
import axios from 'axios'
export default {
    name:'City',
    data(){
        return{
            hotCities:[],
            cities:{},
            letter:''
        }
    },
    components:{
        CityHeader,
        CitySearch,
        CityList,
        CityAlphabet
    },
    methods: {
        getCityInfo(){
            axios.get('/api/city.json')
                .then(this.getCityInfoSucc)
        },
        getCityInfoSucc(res){
            res = res.data;
            if(res.ret&&res.data){
                const data = res.data;
                this.hotCities = data.hotCities;
                this.cities = data.cities;
            }
        },
        handleLetter(value){
            this.letter = value;
        }
    },
   mounted() {
       this.getCityInfo();
   },
}
</script>

<style lang="stylus" scoped>

</style>