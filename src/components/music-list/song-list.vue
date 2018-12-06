<template>
    <div class="song-list" ref="SongList">
        <ul>
            <li v-for="(song,index) in songs" :key="index" class="item">
                <div class="index">{{index+1}}</div>                
                <div class="content">
                    <p class="name">{{song.name}}</p>
                    <p class="des">{{getDesc(song)}}</p>
                </div>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    props:{
        songs:{
            type:Array,
            default:[]
        }
    },
    methods:{
        getDesc(song){
            return `${song.singer} . ${song.album}`
        }
    }
}
</script>

<style lang="scss" scoped>
@import '~common/css/mixin';
.song-list{
    position: relative;
    top:px2rem(10);
    left:0;
    width:100%;
    height:100%;
    overflow: hidden;
    .item{
        display: flex;
        height:px2rem(60);
        @include  border-1px(#e4e4e4);
        .index{
            flex:0 0 px2rem(50);
            font-size: px2rem(16);
            text-align: center;
            line-height: px2rem(60);
            color:#757575;
        }
        .content{
            flex:1;
            .name{
                font-size: px2rem(20);
                padding-top:px2rem(10);
                width:80%;
                @include no-warp();
                color:#2e3030;
            }
            .des{
                font-size:px2rem(12);
                line-height: px2rem(20);
                @include no-warp();
                color:#757575;
            }
        }
    }
}
</style>
