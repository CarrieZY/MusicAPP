<template> 
<div class="songlist">
    <h4>{{title}}</h4>
    <ul>
        <li v-for="(item,index) in songList" :key="index" class="pic">
            <div class="pic">
                <img :src="item.picUrl" alt="">
                <div class="icon">
                    <span class="num"><i class="icon-music"></i>{{getNumber(item.accessnum)}}</span>
                    <span class="icon-play"></span>
                </div>
                <div class="des">
                    <p>{{item.songListDesc}}</p>
                    <span>{{item.songListAuthor}}</span>    
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
      songList:[]
  },
  methods:{
      getNumber(num){
          num=num/10000
          return num.toFixed(2)
      }
  }
}
</script>

<style lang="scss" scoped>
@import '~common/css/mixin';
@import '~common/css/icon.scss';
.songlist{
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
             color:#Fff;
             >span{
                 display: inline-block; 
             }
             .num{
                 position: absolute;
                 left:px2rem(5);
                 bottom: px2rem(5);
                 .icon-music{
                    width:px2rem(10);
                    height:px2rem(10);
                    margin-right:px2rem(5); 
                 }
             }
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
              p{
                font-size: px2rem(14);
                line-height: px2rem(18);
                overflow: hidden;
                text-overflow: ellipsis;
                white-space: nowrap;
              }
              span{
                  font-size: px2rem(12);
              }   
           }
       }    
   } 
}
</style>
