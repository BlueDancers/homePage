<template>
  <div id="main" @mousewheel="handleScroll">
    <div class="pages">
      <one v-show="page == 1"></one>
      <two v-show="page == 2"></two>
      <three v-show="page == 3"></three>
      <four v-show="page == 4"></four>
      <five v-show="page == 5"></five>
    </div>
    <div class="left">
      <div v-for="items in pages" :key="items">
        *
      </div>
    </div>    
  </div>
</template>

<script>
import one from './bar/one'
import two from './bar/two'
import three from './bar/three'
import four from './bar/four'
import five from './bar/five'
export default {
  mounted () {
    this.pages = document.getElementsByClassName('pages')[0].childElementCount    //动态获取当前组件数量 也就是pages里面的子元素的数量
  },
  components: {
    one,
    two,
    three,
    four,
    five
  },
  data() {
    return {
      page: 1,   //当前显示组件
      pages: 0   //总组件数
    }
  },
  methods: {
    handleScroll() {
      //鼠标监听事件
      let page = this.page
      if (page != 5) {
        this.page++
      } else {
        this.page = 1
      }
    }
  }
}
</script>

<style lang="less" scoped>
#main {
  .pages {
    position: absolute;
    top: 0;
    left: 0;
    background-color: antiquewhite;
    width: 100%;
    height: 100%;
    margin: 0px;
    padding: 0px;
  }
  .left {
    position: absolute;
    top: 25%;
    left: 2%;
    border: 1px solid black;
    height: 40%;
  }
}
</style>
