<template>
  <div class="header">
    <div class="header-left">
      <div class="iconfont back-icon">&#xe624;</div>
    </div>
    <div class="header-input">
      <span class="iconfont">&#xe632;</span>
      输入城市/景点/游玩主题
    </div>
    <router-link to="/city">
      <div class="header-right">
        {{city}}
      <span class="iconfont arrow-icon">&#xe62d;</span>
    </div>
    </router-link>
  </div>
</template>
<script>
export default {
  name:'HomeHeader',
  props:{
    city:String
  }
}
</script>
<style lang="stylus" scoped>
// 因为在reset中html font-size =50px
// 1rem =50px,且是二倍尺寸，86px应该为43px，为.86rem
  @import '~styles/variables.styl'
  .header
    line-height $headerHeight
    display:flex
    background:$bgColor
    color:#fff
    .header-left
      width .64rem
      float:left
      .back-icon
        text-align:center
        font-size:.4rem
    .header-input
      flex:1
      height:.64rem
      line-height:.64rem
      background:#fff
      margin-top:.12rem
      margin-left:.2rem
      border-radius:.1rem
      color:#ccc
      padding-left:.2rem
    .header-right
      width:1.24rem
      float:right
      text-align:center
      color:#fff
      .arrow-icon
        font-size:.24rem
        margin-left:-.02rem
</style>