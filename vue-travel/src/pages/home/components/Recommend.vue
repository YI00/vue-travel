<template> 
  <div>
    <div class="title">热销推荐</div>
    <ul>
      <li class="item border-bottom" v-for="item of recommendList" :key="item.id">
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
  data(){
    return {
      recommendList:[
        {
          id:'0001',
          imgUrl:'https://imgs.qunarzz.com/sight/p0/1804/1a/1a48cc20b0d6ed44a3.img.jpg_200x200_32e22bed.jpg',
          desc:'浪漫大连首站，浪漫的海洋主题乐园',
          title:"大连圣亚海洋世界"
        },
        {
          id:'0002',
          imgUrl:'https://imgs.qunarzz.com/sight/p0/1804/1a/1a48cc20b0d6ed44a3.img.jpg_200x200_32e22bed.jpg',
          desc:'浪漫大连首站，浪漫的海洋主题乐园',
          title:"大连圣亚海洋世界"
        },
        {
          id:'0003',
          imgUrl:'https://imgs.qunarzz.com/sight/p0/1804/1a/1a48cc20b0d6ed44a3.img.jpg_200x200_32e22bed.jpg',
          desc:'浪漫大连首站，浪漫的海洋主题乐园',
          title:"大连圣亚海洋世界"
        },
        {
          id:'0004',
          imgUrl:'https://imgs.qunarzz.com/sight/p0/1804/1a/1a48cc20b0d6ed44a3.img.jpg_200x200_32e22bed.jpg',
          desc:'浪漫大连首站，浪漫的海洋主题乐园',
          title:"大连圣亚海洋世界"
        },
        {
          id:'0005',
          imgUrl:'https://imgs.qunarzz.com/sight/p0/1804/1a/1a48cc20b0d6ed44a3.img.jpg_200x200_32e22bed.jpg',
          desc:'浪漫大连首站，浪漫的海洋主题乐园',
          title:"大连圣亚海洋世界"
        },
        {
          id:'0006',
          imgUrl:'https://imgs.qunarzz.com/sight/p0/1804/1a/1a48cc20b0d6ed44a3.img.jpg_200x200_32e22bed.jpg',
          desc:'浪漫大连首站，浪漫的海洋主题乐园',
          title:"大连圣亚海洋世界"
        }
      ]
    }
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