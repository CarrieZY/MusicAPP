<template>
    <div>
        <swiper :options="swiperOption" >
        <swiper-slide v-for="(pic,index) in pics" :key="index">
            <img :src="pic.picUrl" alt="" class="slider-img">
        </swiper-slide>
        <div class="swiper-pagination"  slot="pagination"></div>
        </swiper>
    </div>
</template>

<script>
import 'swiper/dist/css/swiper.css'
import { swiper, swiperSlide } from 'vue-awesome-swiper'
import { getRecommend } from 'api/recommend.js'
import {ERR_OK} from 'api/config'
export default {
    components:{
        swiper,
        swiperSlide
    },
    data(){
        return {
            pics:[],
            swiperOption:{
                pagination: {
                    el: '.swiper-pagination'
                }
            }
        }
    },
    created(){
        this._getRecommend()
    },
    methods:{
        _getRecommend(){
            getRecommend().then((res) =>{
                if(res.code === ERR_OK){
                    this.pics = res.data.slider
                    console.log(this.pics)
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
