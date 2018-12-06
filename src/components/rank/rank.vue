<template>
    <div class="rank">
        <div class="rank-pic"></div>
        <div class="rank-info"></div>
    </div>
</template>

<script>
export default {
    
}
</script>

<style lang="scss" scoped>
.rank{
    display:flex;
    width:98%;
    background: #fff;
    .rank-pic{
        flex:0 0 30%;
        display: inline-block;
        background:rgba(0,0,0,.5);
    }
    .rank-info{
        flex:1;
        display: inline-block;
    }
}
</style>
