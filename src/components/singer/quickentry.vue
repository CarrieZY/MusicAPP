<template>
    <div class="quick" >
        <ul>
            <li v-for="(item,index) in shortcutList" :key="index">{{item}}</li>
        </ul>
    </div>
</template>

<script>
export default {
    props:{
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
    }
}
</script>

<style lang="scss" scoped>
@import '~common/css/mixin';
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
</style>
