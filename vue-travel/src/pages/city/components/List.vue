<template>
  <div class="list" ref="wrapper">
    <div>
      <div class="area">
      <div class="title border-topbottom">当前城市</div>
      <div class="button-list">
        <div class="button-wrapper">
          <div class="button">{{$store.state.city}}</div>
        </div>
      </div>
    </div>
    <div class="area">
      <div class="title border-topbottom">热门城市</div>
      <div class="button-list">
        <div 
            class="button-wrapper" 
            v-for="item of hot" 
            :key="item.id"
            @click="handleChangeCity(item.name)"
        >
          <div class="button">{{item.name}}</div>
        </div>
      </div>
    </div>
    <div class="area" 
         v-for="(items,key) of cities" 
         :key="key"
         :ref="key"
    >
      <div class="title border-topbottom">
        {{key}}
      </div>
      <div class="item-list">
        <div class="item border-bottom"
             v-for="item of items" 
             :key="item.id"
             @click="handleChangeCity(item.name)"
        >
          {{item.name}}
        </div>
      </div>
    </div>
    </div>
  </div>
</template>
<script>
import Bscroll from 'better-scroll'
export default {
  name:'CityList',
  props:{
    cities:Object,
    hot:Array,
    letter:String
  },
  mounted(){
    this.scroll = new Bscroll(this.$refs.wrapper)
  },
  methods:{
    handleChangeCity(city){
      this.$store.commit('changeCity',city)
      this.$router.push('/')
    }
  },
  watch:{
    letter(){
      if(this.letter){
        const element = this.$refs[this.letter][0]
        // console.log(element)
        this.scroll.scrollToElement(element)
      }
    }
  }
}
</script>
<style lang="stylus" scoped>
  @import '~styles/variables.styl'
  .border-topbottom
    &:before
      border-color:#ccc
    &:after
      border-color:#ccc
  .border-bottom
  &:before
    border-color:#ccc
  .list
    position:absolute
    top:1.58rem
    left:0
    right:0
    bottom:0
    overflow hidden
    .title
      height:.54rem
      line-height:.44rem
      background:#eee
      padding-left:.2rem
      color:#666
      font-size:.26rem
    .button-list
      padding:.1rem
      overflow hidden
      padding:.1rem .6rem .1rem .1rem
      .button-wrapper
        float:left
        width:33.33%
        .button
          padding:.1rem 0 
          border-radius:.08rem
          margin:.1rem
          text-align:center
          border:.02rem solid #ccc
    .item-list
      .item
        paddind 0.1rem
        line-height:.76rem
        color:#666
        padding-left:.2rem
</style>