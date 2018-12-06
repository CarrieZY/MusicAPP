<template>
    <div class="music-list">
        <div class="back" ref="back">
            <i class="icon-back"></i>
            <h1 class="title" v-html="title"></h1>
        </div>
        <div class="list-warpper" ref="ListWarpper">
            <div>
                <!-- 这里图片时背景图片 所以要用：style来写 -->
                <div class="bg-image" :style="bgstyle" ref="bgimage">
                    <div class="filter"></div>
                </div>
                <song-list :songs="songs"></song-list>
            </div>
        </div>
        
    </div>
</template>

<script>
import BScroll from 'better-scroll'
import SongList from './song-list'
export default {
    components:{
        SongList
    },
    props:{
        songs:{
            type:Array,
            default:[]
        },
        title:{
            type:String,
            default:''
        },
        bgImage:{
            type:String,
            default:''
        }
    },
    mounted(){
        this.scroll= new BScroll(this.$refs.ListWarpper)
    },
    computed:{
        bgstyle() {
            return `background-image:url(${this.bgImage})`
        }
    }
}
</script>

<style lang="scss" scoped>
@import '~common/css/mixin';
@import '~common/css/icon';
.music-list{
    position: fixed;
    z-index:100;
    top:0;
    width:100%;
    height:100%;
    background: #f2f3f4;
    .back{
        position: fixed;
        top:0;
        width:100%;
        height:px2rem(40);
        left:px2rem(6);
        color:#fff;
        z-index:102;
        display: flex;
        .icon-back{
            flex:0 0 px2rem(50);
            padding: px2rem(10);
            display: block;
        }
        .title{
            flex:1;
            @include no-warp();
            text-align: center;
            line-height:px2rem(40);
            color:#fff;
            font-weight: 600;
        }
    }
    .list-warpper{
        position: relative;
        width:100%;
        height:100%;
        overflow: hidden;
        .bg-image{
            position: relative;
            padding-top:70%;
            width:100%;
            height:0;
            transform-origin: top;
            background-size: cover;
        }  
    }
    
}
</style>
