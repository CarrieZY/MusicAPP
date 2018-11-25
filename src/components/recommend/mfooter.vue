<template>
    <div class="footer">
        <div class="logo">Music APP</div>
        <p>Copyright © 1998 - 2018  Tencent. All Rights Reserved.</p>
        <p>联系电话：0755-86013388 QQ群：55209235</p>
    </div>
</template>

<script>
export default {
    
}
</script>

<style lang="scss" scoped>
@import '~common/css/mixin.scss';
@import '~common/css/variable';
.footer{
   width:100%;
   padding-bottom: px2rem(30);
   .logo{
       color:$color-text;
       font-weight: 700;
       font-size: px2rem(20);
       line-height:px2rem(30);
       text-align: center;
       padding-top:px2rem(20);
   }
   >p{
       font-size:px2rem(10);
       line-height: px2rem(18);
       color:rgba(0, 0, 0,.5);
       text-align: center;
   }
}
</style>
