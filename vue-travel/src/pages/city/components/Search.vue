<template>
  <div>
    <div class="search">
      <input v-model="keywords" class="search-input" type="text" placeholder="输入城市名或拼音">
    </div>
    <div class="search-content" ref="search" v-show="keywords">
      <ul>
        <li class="search-item border-bottom" 
            v-for="item of list" 
            :key="item.id"
            @click="handleChangeCity(item.name)"
        >
          {{item.name}}
        </li>
        <li class="search-item border-bottom" v-show="hasNoData">没有找到匹配数据</li>
      </ul>
    </div>
  </div>
</template>
<script>
import Bscroll from 'better-scroll'
export default {
  name:'CitySearch',
  props:{
    cities:Object
  },
  data(){
    return {
      keywords:'',
      list:[],
      timer:null
    }
  },
  methods:{
    handleChangeCity(city){
      this.$store.commit('changeCity',city)
      this.$router.push('/')
    }
  },
  watch:{
    keywords(){
      if(this.timer){
        clearTimeout(this.timer)
      }
      if(!this.keywords){
        this.list = []
        return 
      }
     this.timer = setTimeout(() => {
        const res = []
        for(let i in this.cities){
          this.cities[i].forEach(value => {
            if(value.spell.indexOf(this.keywords)>-1||
               value.name.indexOf(this.keywords)>-1){
                 res.push(value)
               }
          });
        }
        this.list = res
      }, 100);
    }
  },
  computed:{
    hasNoData(){
      return !this.list.length
    }
  },
  mounted(){
    this.scroll = new Bscroll(this.$refs.search)
  }
}
</script>
<style lang="stylus" scoped>
  @import '~styles/variables.styl'
  .search
    background:$bgColor
    height:.72rem
    padding:0 .1rem
    .search-input
      box-sizing:border-box
      width:100%
      height:.62rem
      line-height:.62rem
      padding:0 .1rem
      text-align:center
      border-radius:.06rem
      color:#666
  .search-content
    z-index:1
    position:absolute
    overflow:hidden
    top:1.58rem
    left:0
    right:0
    bottom:0
    background:#eee
    .search-item
      line-height:.62rem
      padding-left:.2rem
      color:#666
      background:#fff
</style>