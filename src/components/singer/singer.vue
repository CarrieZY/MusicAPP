<template>
    <div class="singer">
        <listview :data="singers" 
        @select="selectSinger"></listview>
        <router-view></router-view>
        <div v-show="!singers.length">
            <loading></loading>
        </div>
    </div>
</template>

<script>
import { getSongList } from 'api/singer'
import {ERR_OK} from 'api/config'
import Singer from 'common/js/singer'
import listview from './listview'
import loading from './loading/loading'
import { mapMutations } from 'vuex'
const HOT_SINGER_LEN = 10
const HOT_NAME = '热门'
export default {
    components:{
        listview,
        loading
    },
    data(){
        return {
            singers:[]
        }
    },
    created(){
        this._getSongList()
    },
    methods:{
        selectSinger(singer){
            this.$router.push({
                path:`/singer/${singer.id}`
            })
            this.setSinger(singer)
        },
        _getSongList(){
            getSongList().then((res) =>{
                if(res.code === ERR_OK){
                    this.singers = this._normalizeSinger(res.data.list)
                    console.log(this.singers)
                }
            })
        },
        _normalizeSinger(list) {
            let map = {
            hot: {
                title: HOT_NAME,
                items: []
            }
            }
            list.forEach((item, index) => {
            if (index < HOT_SINGER_LEN) {
                map.hot.items.push(new Singer({
                name: item.Fsinger_name,
                id: item.Fsinger_mid
                }))
            }
            const key = item.Findex
            if (!map[key]) {
                map[key] = {
                title: key,
                items: []
                }
            }
            map[key].items.push(new Singer({
                name: item.Fsinger_name,
                id: item.Fsinger_mid
            }))
            })
            // 为了得到有序列表，我们需要处理 map
            let ret = []
            let hot = []
            for (let key in map) {
            let val = map[key]
            if (val.title.match(/[a-zA-Z]/)) {
                ret.push(val)
            } else if (val.title === HOT_NAME) {
                hot.push(val)
            }
            }
            ret.sort((a, b) => {
            return a.title.charCodeAt(0) - b.title.charCodeAt(0)
            })
            return hot.concat(ret)
        },
        ...mapMutations({
            setSinger:'SET_SINGER'
        })

    }    
}
</script>

<style lang="scss" scoped>
@import '~common/css/mixin.scss';
.singer{
    position: fixed;
    top:px2rem(85);
    left:0;
    bottom: 0;
    width:100%;
    height:100%;
}
</style>
