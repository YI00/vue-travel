<template> 
  <div>
    <div class="title">热销推荐</div>
    <ul>
      <li class="item border-bottom" v-for="item of list" :key="item.id">
        <img class="item-img" :src="item.imgUrl" alt="">
        <div class="item-info">
          <p class="item-title">{{item.title}}</p>
          <p class="item-desc">{{item.desc}}</p>
          <button class="item-button">查看推荐</button>
        </div>
      </li>
    </ul>
  </div>
</template>
<script>
export default{
  name:'HomeRecommend',
  props:{
    list:Array
  }
}
</script>
<style lang="stylus" scoped>
  @import '~styles/mixins.styl'
  .title
    margin-top:.2rem
    line-height:.8rem
    background:#eee
    text-indent:.2rem
  .item
    height 1.9rem
    display:flex
    overflow:hidden
    .item-img
      padding:.1rem
      width:1.7rem
      height:1.7rem
    .item-info
      flex:1
      padding:.2rem
      min-width:0
      .item-title:
        line-height:.54rem
        font-size:.32rem
        ellipsis()
      .item-desc
        line-height:.4rem
        color:#ccc
        ellipsis()
      .item-button
        line-height:.44rem
        margin-top:.4rem
        background:#ff9300
        padding:0 .2rem
        border-radius:.06rem
        color:#fff
</style>