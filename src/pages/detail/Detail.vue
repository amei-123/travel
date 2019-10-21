<template>
    <div>
        <detail-banner 
            v-bind:sightName="sightName"
            v-bind:bannerImg="bannerImg"
            v-bind:bannerImgs="gallaryImgs"
        ></detail-banner>
        <detail-header></detail-header>
        <detail-list v-bind:List="List"></detail-list>
        <div class="content"></div>
    </div>
</template>

<script>
import DetailBanner from './components/banner'
import DetailHeader from './components/header'
import DetailList from './components/list'
import axios from 'axios'
export default {
    name:'Detail',
    components:{
        DetailBanner,
        DetailHeader,
        DetailList
    },
    data(){
        return{
            sightName:'',
            bannerImg:'',
            gallaryImgs:[],
            List:[]
        }
    },
    methods:{
        getDetailData(){
            axios.get('/api/detail.json',{
                params:{
                    id:this.$route.params.id
                }
            })
                .then(this.handleDetailData)
        },
        handleDetailData(res){
            res = res.data;
            if(res.ret && res.data){
                const data = res.data;
                this.sightName = data.sightName;
                this.bannerImg = data.bannerImg;
                this.gallaryImgs = data.gallaryImgs;
                this.List = data.categoryList;
            }
        }
    },
    mounted() {
        this.getDetailData()
    },
}
</script>

<style lang="stylus">
    .content
        height :40rem
</style>