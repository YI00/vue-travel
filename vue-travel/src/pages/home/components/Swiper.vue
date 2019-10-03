<template>
   <div class="wrapper">
      <swiper :options="swiperOption">
        <swiper-slide v-for="item of swiperList" :key="item.id">
          <img class="swiper-img" :src="item.imgUrl" alt="">
        </swiper-slide>
        <div class="swiper-pagination"  slot="pagination"></div>
      </swiper>
   </div>
</template>
<script>
export default {
  name:'HomeSwiper',
  data(){
    return {
      swiperOption:{
        pagination:'.swiper-pagination',
        loop:true
      },
      swiperList:[
        {
          id:'0001',
          imgUrl:"https://mp-piao-admincp.qunarzz.com/mp_piao_admin_mp_piao_admin/admin/20199/839ae28f89f78168f17aaa4f137c7d42.jpg_750x200_598f53cb.jpg"
        },
        {
          id:'0002',
          imgUrl:'https://mp-piao-admincp.qunarzz.com/mp_piao_admin_mp_piao_admin/admin/20199/47f7d9e9fb7c5cb88a1245180c9ca5b4.jpg_750x200_de4858e1.jpg'
        }
      ]
    }
  }
}
</script> 
<style lang="stylus" scoped>
// 因为直接写.swiper-pagination-bullet-active没有用
// 因为是scoped,而这个轮播图实际的样式是在swiper上，所以这里写没用
// 要加>>>,表示样式穿透，只要wrapper下出现.swiper-pagination-bullet-active,要遵循这样的样式
// 这样就不受scoped限制
  .wrapper >>> .swiper-pagination-bullet-active
    background:#fff
  .wrapper
    // 这个样式是为了让轮播图占位
    // 否则没有占位的话，轮播图下面还有内容
    // 轮播图加载时突然出现，会发生抖动
    // 这是固定写法，除了padding-bottom:31.25%,这个数字是宽高比
    // 如果不想这样写，可以width:0,height:31.25vw,但是可能有兼容性问题
    width:100%
    height:0
    overflow:hidden
    padding-bottom:31.25%
    background-color #eee
    .swiper-img
      width:100%
</style>