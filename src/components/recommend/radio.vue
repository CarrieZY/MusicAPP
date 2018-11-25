<template> 
<div class="radio">
    <h4>{{title}}</h4>
    <ul>
        <li v-for="(item,index) in radioList" :key="index" class="pic">
            <div class="pic">
                <img :src="item.picUrl" alt="">
                <div class="icon">
                    <span class="icon-play"></span>
                </div>
                <div class="des">
                    <p>{{item.Ftitle}}</p>    
                </div>
            </div>                
        </li>
    </ul>
</div>   
</template>

<script>
export default {
  props:{
      title:'',
      radioList:[]
  }
}
</script>

<style lang="scss" scoped>
@import '~common/css/mixin';
@import '~common/css/icon.scss';
.radio{
    margin-top:px2rem(11);
   >h4{
       margin-bottom: px2rem(11);
       font-size:px2rem(16);
       margin-left:1.25%;
   }
   ul li{
       display: inline-block;
       width:50%;
       overflow: hidden;
       .pic{
          width:95%;
          margin-left:2.5%;
          background:#fff;
          >img{
           width:100%;
          }
          .icon{
             position: relative; 
             width:100%;
             height:px2rem(43);
             margin-top:px2rem(-43);
             .icon-play{
                color:#444;
                position: absolute;
                bottom: px2rem(5);
                right:px2rem(5);
                width:px2rem(24);
                height: px2rem(24);  
             }
          }
          .des{
            padding: 0 px2rem(7) px2rem(5);
            >p{
                font-size: px2rem(14);
                line-height: px2rem(18);
                height:px2rem(36);
                overflow: hidden;
                text-overflow: ellipsis;
                white-space: nowrap;
            }
           }
       }    
   } 
}
</style>
