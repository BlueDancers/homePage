<template>
  <div id="main" @mousewheel="handleScroll" @mousedown="mousedown" @mouseup="mouseup">
    <div class="pages">
        <transition :name="deltay > 0?'faded':'fades'">
          <one v-show="page == 1"></one>
        </transition>
        <transition :name="deltay > 0?'faded':'fades'">
          <two v-show="page == 2"></two>
        </transition>
        <transition :name="deltay > 0?'faded':'fades'">
          <three v-show="page == 3"></three>
        </transition>
        <transition :name="deltay > 0?'faded':'fades'">
          <four v-show="page == 4"></four>
        </transition>
        <transition :name="deltay > 0?'faded':'fades'">
          <five v-show="page == 5"></five>
        </transition>
        <transition :name="deltay > 0?'faded':'fades'">
          <six v-show="page == 6"></six>
        </transition>
    </div>
    <div class="left">
      <ul>
        <li v-for="items in pages" :class="items == page?'active':' '" :key="items">
          <span @click="gotoPage(items)"></span>
        </li>
      </ul>
    </div>    
  </div>
</template>

<script>
import one from './bar/one'
import two from './bar/two'
import three from './bar/three'
import four from './bar/four'
import five from './bar/five'
import six from './bar/six'
export default {
  mounted() {
    this.pages = document.getElementsByClassName('pages')[0].childElementCount //动态获取当前组件数量 也就是pages里面的子元素的数量
  },
  components: {
    one,
    two,
    three,
    four,
    five,
    six
  },
  data() {
    return {
      page: 1, //当前显示组件
      pages: 0, //总组件数
      deltay: 0, //鼠标前后滚动事件
      mousedownevent: 0,
      mouseupevent: 0
    }
  },
  methods: {
    throttle(method) {   //函数节流
      clearTimeout(method.tId)
        method.tId = setTimeout(function(){
            method();
        }, 200);
    },
    handleScroll(e) {
      //鼠标监听事件
      //判断鼠标前后滚动
      
      this.deltay = e.deltaY || e
      this.throttle(this.scrollevent)
      //this.scrollevent()
    },
    scrollevent() {
      if (this.deltay > 0) {
        //鼠标向下滚动
        let page = this.page
        if (page != this.pages) {
          this.page++
        } else {
          this.page = 1
        }
      } else {
        let page = this.page
        if (page != 1) {
          this.page--
        } else {
          this.page = this.pages
        }
      }
    },
    gotoPage(item) {
      console.log(item)
      this.page = item
    },
    mousedown(e) {
      this.mousedownevent = e.screenY
    },
    mouseup(e) {
      this.mouseupevent = e.screenY
      let result = -(this.mouseupevent - this.mousedownevent)
      //因为还要防止不小心触碰事件
      if (result > 0) {
        //在handleScroll里面设置>0是向下滚动,所以应该是数据应该取反处理一下
        console.log(result)
        if (result > 80) {
          this.handleScroll(result)
        }
      } else {
        if (result < -80) {
          this.handleScroll(result)
          console.log('上拉事件')
        }
      }
    }
  }
}
</script>

<style lang="less" scoped>
#main {
  .pages {
     //禁止滚动条的出现
    overflow-x:hidden;
    overflow-y:hidden;
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    margin: 0px;
    padding: 0px;
  }
  .left {
    position: absolute;
    top: 25%;
    left: 2%;
    height: 40%;
    display: flex;
    align-items: center;
    ul {
      li {
        span {
          display: flex;
          margin: 15px 0px;
          width: 8px;
          height: 8px;
          border: 1px solid black;
          border-radius: 50%;
        }
      }
    }
  }
}
.active {
  background-color: black;
  border-radius: 50%;
}

.faded-enter-active,
.faded-leave-active {
  //在离开和进入时候的动画时间
  transition: all .6s;
}
.faded-enter {
  //进入变成显示
  transform: translateY(100%);
}
.faded-leave-to {
  transform: translateY(-100%); //离开时变成透明
}

.fades-enter-active,
.fades-leave-active {
  //在离开和进入时候的动画时间
  transition: all .6s;
}
.fades-enter {
  //进入变成显示
  transform: translateY(-100%);
}
.fades-leave-to {
  transform: translateY(100%);
}
</style>
