<template>
<div class="wrap">
    <div class="listview" ref="listview" :data="data">
        <ul class="content">
        <li v-for="(value, index) in data" :key="index" ref="listGroup">
            <h2 class="title">{{value.title}}</h2>
            <ul>
            <li v-for="(item, index) in value.items" :key="index" class="singer-item" @click="selectItem(item)">
            <img v-lazy="item.avatar" class="singerPic">
                <span class="singer-name">{{item.name}}</span>
            </li>
            </ul>
        </li>
        </ul>
    </div>
    <div class="quick" >
        <ul>
            <li v-for="(item,index) in shortcutList" :key="index" @click="LettersClick"
             :data-index="index">{{item}}</li>
        </ul>
    </div>
</div>    
</template>

<script>
import BScroll from 'better-scroll'
import { getData } from 'common/js/dom'
export default {
    props: {
        data:{
            type:Array,
            default:''
        }
    },
    computed:{
        shortcutList(){
            return this.data.map((value) =>{
                return value.title.substr(0,1)
                console.log('value.title')
            })
        }
    },
    mounted(){
        this.scroll= new BScroll(this.$refs.listview)
    },
    methods:{
        selectItem(item){
            this.$emit('select',item)
        },
        LettersClick(e){
            let index = getData(e.target,'index')
            this.scroll.scrollToElement(this.$refs.listGroup[index],0) 
            console.log(e.target.innerText)
        }
    }
}
</script>

<style lang="scss">
@import '~common/css/mixin';
.wrap{
    width:100%;
    height:100%;
}
.quick{
    position: fixed;
    top:50%;
    right:0;
    transform: translate(0,-25%);
    ul li{
        font-size: px2rem(12);
        width:px2rem(15);
        height:px2rem(15);
        text-align: center;
        line-height: px2rem(15);
    }
}
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
