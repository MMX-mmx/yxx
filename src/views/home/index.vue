<template>
  <div class="box">
      <div id="banner">
          <!-- 轮播图插件 -->
          <van-swipe :autoplay="3000">
              <van-swipe-item v-for="(item,index) in banner" :key="index"><img :src="item.picUrl"/></van-swipe-item>
          </van-swipe>
          <div class="icons">
              <div class="icon-item" >
                  <van-icon name="like" size="30"/>
                  <p>签到</p>
              </div>
              <div class="icon-item">
                  <van-icon name="gift" size="30"/>
                  <p>礼券</p>
              </div>
              <div class="icon-item">
                  <van-icon name="coupon" size="30"/>
                  <p>砍价</p>
              </div>
              <div class="icon-item">
                  <van-icon name="label" size="30" />
                  <p>专栏</p>
              </div>
          </div>
      </div>
  </div>
</template>

<script>
export default {
  name: '',
  mounted() {
      this.getBanners();
  },
  data() {
    return {
        banner:[],
    };
  },
  computed:{
  },
  methods: {
      //获取banner图的嘻嘻你
      getBanners(){
          this.$axios({
              url:"/banner/list",
          }).then(res=>{
              console.log(res);
              this.banner = res.data;
          })
      }
  },
};
</script>

<style scoped lang="scss">
.box{
    width: 100%;
    background: #F0F0F0;
    #banner{
        width: 100%;
        position: relative;
        img{
            width: 100%;
        }
        .icons{
            width: 100%;
            height: 2rem;
            background: #FFF;
            position: absolute;
            bottom:0px;
            display: flex;
            justify-content: space-around;
            border-top-left-radius: .3rem;
            border-top-right-radius: .3rem;
            align-items: center;
            p{
                text-align:center;
                margin-top: .2rem;
                font-size: .4rem;
            }
        }
    }
}
</style>