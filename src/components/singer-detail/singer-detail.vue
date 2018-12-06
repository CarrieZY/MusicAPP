<template>
<transition name="slider">
    <music-list :songs="songs" :title="title" :bg-image="bgImage"></music-list>
</transition>    
</template>

<script>
import MusicList from 'components/music-list/music-list'
import { mapGetters } from 'vuex'
import { getSingerDetail } from 'api/singer'
import {createSong } from 'common/js/song'
import {ERR_OK} from 'api/config'
export default {
    components:{
        MusicList
    },
    data(){
        return {
            songs:[]
        }
    },
    computed:{
        title(){
            return this.singer.name
        },
        bgImage(){
            return this.singer.avatar
        },
        ...mapGetters([
         'singer'
        ])
    },
    created (){
        this._getDetail()
        console.log(this.singer)
    },
    methods:{
       _getDetail(){
           if(!this.singer.id){
               this.$router.push('/singer')
               return
           }
           getSingerDetail(this.singer.id).then((res) =>{
               if(res.code === ERR_OK){
                   this.songs=this._normalizeSongs(res.data.list)
                   console.log(this.songs)
               }
           })
       },
       _normalizeSongs(list){
           let ret =[]
           list.forEach((item) => {
               let { musicData } =item
               if(musicData.songid && musicData.songmid){
                   ret.push(createSong(musicData))
               }
           })
           return ret
       } 
    } 
}
</script>

<style lang="scss">
@import '~common/css/mixin';
.slider-enter-active,.slider-leave-active{
    transition: all .3s;
}
.slider-enter,.slider-leave-to{
    transform: translate3d(100%,0,0);
}
</style>

