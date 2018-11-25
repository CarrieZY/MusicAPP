<template>
    <div>
        <swiper :options="swiperOption" >
        <swiper-slide v-for="(pic,index) in pics" :key="index">
            <img :src="pic.picUrl" alt="" class="slider-img">
        </swiper-slide>
        <div class="swiper-pagination"  slot="pagination"></div>
        </swiper>
        <radio :radioList="radioList" title="电台"/>
        <song-list :songList="songList" title="热门歌单"></song-list>
        <Mfooter/>
    </div>
</template>

<script>
import 'swiper/dist/css/swiper.css'
import { swiper, swiperSlide } from 'vue-awesome-swiper'
import { getRecommend,getDistList} from 'api/recommend.js'
import {ERR_OK} from 'api/config'
import radio from './radio'
import songList from './songList'
import Mfooter from './mfooter'
export default {
    components:{
        swiper,
        swiperSlide,
        radio,
        songList,
        Mfooter
    },
    data(){
        return {
            pics:[],
            radioList:[],
            songList:[],
            swiperOption:{
                pagination: {
                    el: '.swiper-pagination'
                }
            }
        }
    },
    created(){
        this._getRecommend()
        this._getDistList()
    },
    methods:{
        _getRecommend(){
            getRecommend().then((res) =>{
                if(res.code === ERR_OK){
                    this.pics = res.data.slider
                    this.radioList=res.data.radioList
                    this.songList=res.data.songList
                    console.log(this.pics)
                }                
            })
        },
        _getDistList(){
            getDistList().then((res) =>{
                if(res.code === ERR_OK){
                    // this.radioList=res.data.radioList
                    // console.log(res.data.radioList)
                }
            })
        }
    }
}
</script>

<style lang="scss" scoped>
.slider-img{
    width:100%;
    height: px2rem(317);
}
</style>
