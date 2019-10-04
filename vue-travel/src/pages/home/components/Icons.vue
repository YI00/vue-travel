<template>
  <div class="icons">
     <swiper>
        <swiper-slide v-for="(page,index) of pages" :key="index">
          <div class="icon"
               v-for="item of page"
               :key="item.id"
          >
            <div class="icon-img">
              <img class="icon-img-content" :src="item.imgUrl" alt="">
            </div>
            <p class="icon-desc">{{item.desc}}</p>
          </div>
        </swiper-slide>
     </swiper>
  </div>
</template>
<script>
export default {
  name:'HomeIcons',
  data(){
    return {
      iconsList:[
        {
          id:'0001',
          imgUrl:"https://imgs.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png",
          desc:"景点门票"
        },
        {
          id:'0002',
          imgUrl:"https://imgs.qunarzz.com/piao/fusion/1803/6c/9e54a8540fee0102.png",
          desc:"故宫"
        },
        {
          id:'0003',
          imgUrl:"https://imgs.qunarzz.com/piao/fusion/1804/ff/fdf170ee89594b02.png",
          desc:"北京必游"
        },
        {
          id:'0004',
          imgUrl:"https://imgs.qunarzz.com/piao/fusion/1803/3e/86314b2af03b7502.png",
          desc:"水上乐园"
        },
        {
          id:'0005',
          imgUrl:"https://imgs.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png",
          desc:"景点门票"
        },
        {
          id:'0006',
          imgUrl:"https://imgs.qunarzz.com/piao/fusion/1803/6c/9e54a8540fee0102.png",
          desc:"故宫"
        },
        {
          id:'0007',
          imgUrl:"https://imgs.qunarzz.com/piao/fusion/1804/ff/fdf170ee89594b02.png",
          desc:"北京必游"
        },
        {
          id:'0008',
          imgUrl:"https://imgs.qunarzz.com/piao/fusion/1803/3e/86314b2af03b7502.png",
          desc:"水上乐园"
        },
        {
          id:'0009',
          imgUrl:"https://imgs.qunarzz.com/piao/fusion/1803/b6/37560ece9c62b502.png",
          desc:"奥林匹克塔"
        }
      ]
    }
  },
  computed:{
    pages(){
      const pages = []
      this.iconsList.forEach((item,index) => {
        const page = Math.floor(index/8)
        if(!pages[page]){
          pages[page] = []
        }
        pages[page].push(item)
      })
      return pages
    }
  }
}
</script>
<style lang="stylus" scoped>
@import '~styles/variables.styl'
@import '~styles/mixins.styl'
  .icons >>> .swiper-container
    height:0
    padding-bottom:50%
  .icons
    margin-top:.1rem
    .icon
        position:relative
        overflow hidden
        float left
        width:25%
        height:0
        padding-bottom:25%
        // background:blue
        .icon-img
          position:absolute
          top:0
          left:0
          right:0
          bottom:.44rem
          // background:blue
          .icon-img-content
            display:block
            height:100%
            margin:0 auto 
        .icon-desc
          position:absolute
          left:0
          right:0
          bottom:0
          height:.44rem
          line-height:.44rem
          color:$darkTextColor
          text-align:center  
          ellipsis()
</style>