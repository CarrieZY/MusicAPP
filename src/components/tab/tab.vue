<template>
    <div class="tab">
        <router-link tag="a" to="/recommend">推荐</router-link>
        <router-link tag="a" to="/rank">排行</router-link>
        <router-link tag="a" to="/singer">歌手</router-link>
        <router-link tag="a" to="/search">搜索</router-link>
    </div>
</template>

<script>
export default {
    
}
</script>

<style lang="scss" scoped>
@import '~common/css/mixin';
@import '~common/css/variable';
.tab{
    width:100%;
    display: flex;
    height:px2rem(40);
    line-height: px2rem(40);
    @include border-1px(#ccc);
    background:#fff;
    >a{
        text-decoration: none;
        color:#666;
        flex:1;
        text-align: center;
        justify-content:space-around; //两边空隙均匀分布
        &.router-link-active{
            color:$color-text;
            font-weight:600;
            border-bottom: 2px solid $color-text;
        }
    }  
}
</style>
