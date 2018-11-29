<template>
    <div class="listview" ref="listview">
        <ul class="content">
        <li v-for="(value, index) in data" :key="index" ref="listGroup">
            <h2 class="title">{{value.title}}</h2>
            <ul>
            <li v-for="(item, index) in value.items" :key="index" class="singer-item" @click="selectItem(item)">
            <img :src="item.avatar" class="singerPic">
                <span class="singer-name">{{item.name}}</span>
            </li>
            </ul>
        </li>
        </ul>
    </div>
</template>

<script>
import BScroll from 'better-scroll'
export default {
    props: {
        data:{
            type:Array,
            default:''
        }
    },
    mounted(){
        this.scroll= new BScroll(this.$refs.listview)
    },
    methods:{
        selectItem(item){
            this.$emit('select',item)
        }
    }
}
</script>

<style lang="scss">
@import '~common/css/mixin';
.listview{
    position: relative;
    left: 0;
    top: 0;
    overflow: hidden;
    width:100%;
    height:100%;
    .content{
        .title{
            height:px2rem(20);
            line-height:px2rem(20);
            padding-left:px2rem(11);
            font-size: px2rem(14);
        }
        .singer-item{
            background:#fff;
            padding: px2rem(10) px2rem(11);
            .singerPic{
                width:px2rem(50);
                height:px2rem(50);
                border-radius: 50%;
            }
            .singer-name{
                vertical-align: top;
                text-align: center;
                line-height: px2rem(50);
                margin-left:px2rem(10);
            }
        }
    }

}
</style>
