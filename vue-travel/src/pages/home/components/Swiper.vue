<template>
   <div class="wrapper">
      <swiper :options="swiperOption" v-if="showSwiper">
        <swiper-slide v-for="item of list" :key="item.id">
          <img class="swiper-img" :src="item.imgUrl" alt="">
        </swiper-slide>
        <div class="swiper-pagination"  slot="pagination"></div>
      </swiper>
   </div>
</template>
<script>
export default {
  name:'HomeSwiper',
  props:{
    list:Array
  },
  data(){
    return {
      swiperOption:{
        pagination:'.swiper-pagination',
        loop:true
      }
    }
  },
  computed:{
    showSwiper(){
      return this.list.length
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