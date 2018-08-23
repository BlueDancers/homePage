<template>
  <div class="five">
    <div class="header">
      <div class="header-text">
        <p>我的文章</p>
      </div>
    </div> 
    <div class="articleList">
      <div class="article">
        <div class="list" v-for="(item, index) in list" :key="index" @click="goto(item.url)">
          <p class="title">{{ item.title }}</p>
          <p class="text">  &nbsp&nbsp&nbsp&nbsp{{ item.text }}</p>
          <p class="time">
            <img src="../../../static/six/日历.png" alt="">
            <span>{{ item.time }}</span> 
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      list: [
        {
          title: 'JavaScript - 异步的前世今生',
          text:
            '在开始接触JavaScript的时候,书上有一句话我记忆深刻,JavaScript是一门单线程语言,不管从什么途径去获取这个消息,前端开发者都会记住,哦~~,JavaScript是一门单线程语言,所以alert()会卡住为什么JavaScript是一门单线程语言?因为什么原因让JavaScript出生就是单线程语言?提出问题,必然解决问题,从JavaScript出生说起,最开始JavaScript是配合html去完成对dom的控制,优化用户交互,于是问题来了js可以修改Dom结构浏览器渲染Dom结假如同时执行,会发生什么,假如同时操作同一个Dom怎么办,同理 两段js都修改Dom结构,假如同时操作Dom会发生什么js没有执行的时候,浏览器Dom渲染,js执行的时候,浏览器Dom停止渲染,html结构树本来是就是从上往下渲染,也就是说,浏览器渲染Dom本身就是单线程,js为了避免发生Dom冲突,没有办法只能成为单线程语言',
          time: '2018-08-16',
          url: 'https://github.com/vkcyan/text/blob/master/JavaScript/JavaScript%20%E5%BC%82%E6%AD%A5%E7%9A%84%E5%89%8D%E4%B8%96%E4%BB%8A%E7%94%9F.md'
        },
        {
          title: 'cookie sessionStorage localStorage的异同',
          text:
            '本文主要总结一下,这三者的异同点,特性,以及应用场景Cookie在我第一次接触到cookie是在学习javaWeb的时候,主要用途是保存登录信息,比如退出登录,但是跳转到登录的时候,用户名以及写好了,这就是cookie的功劳谈一谈cookie的身世吧,在1993年3月份由网景公司发明,Cookie ,小甜点,cookie真的特别小,只能存4KB的数据cookie的特点虽然存在浏览器,但是一般由服务器生成,可以设置失效时间,如果是浏览器生成的默认浏览器关闭的时候失效很小,4KB用来保存客户浏览器请求服务器页面的请求信息 ,比如登录信息,但是这样也不太好的地方,尤其是多人使用电脑',
          time: '2018-07-20',
          url: 'https://github.com/vkcyan/text/blob/master/JavaScript/cookie%20sessionStorage%20localStorage%E7%9A%84%E5%8C%BA%E5%88%AB.md'
        },
        {
          title: '第一次使用mpvue的记录',
          text:
            '​昨晚睡前打开了半个月没打开的知乎, 看到了一个专栏文章再见jquery,我的老朋友,突然想到之前github传出,github已经彻底删除jquery,这似乎标志着前端已经完全进入了一个新的时代,js从最开始的小丑语言,现在已经成为一个非常优秀的编程语言,开发者的目光从兼容性一步步的转向了模块化',
          time: '2018-08-05',
          url: 'https://github.com/vkcyan/text/blob/master/JavaScript/%E7%AC%AC%E4%B8%80%E6%AC%A1%E4%BD%BF%E7%94%A8mpvue%E7%9A%84%E8%AE%B0%E5%BD%95.md'
        },
        {
          title: 'call apply的模拟实现',
          text:
            '​call apply的功能类似,先从call说起,借助大神的话: call()方法在使用一个指定this值和若干个指定的参数值的前提下调用某个函数和方法(真的难理解)',
          time: '2018-7-31',
          url:'https://github.com/vkcyan/text/blob/master/JavaScript/call%20apply%E7%9A%84%E6%A8%A1%E6%8B%9F%E5%AE%9E%E7%8E%B0.md'
        },
        {
          title: 'Vue路由钩子的总结',
          text: '使用vue已经有一段是时间了,这不断的写项目里面,基本上清楚了vue的这种与jq完成不一样的思想,越是研究越是感觉作者之强大,对vue SPA单页面里面最常用的vue-router组件,今天就谈谈这个,我使用的经验vue-router作为vue里面最基础的服务,学习一段时间,对遇到的需求进行一些总结使用vue-cli作为开发前提 vue-router已经配置好了',
          time: '2018-07-17',
          url: 'https://github.com/vkcyan/text/blob/master/Vue/vue%20%E8%B7%AF%E7%94%B1%E9%92%A9%E5%AD%90afterEach%20beforeEach.md'
        },
        {
          title: 'JavaScript深入之原型与原型链',
          text: '今天看了github上面的某位大佬对原型与原型链的文章 讲解很透彻原型与原型链prototype每个函数都有prototype属性,如下',
          time: '2018-3-18',
          url: 'https://github.com/vkcyan/text/blob/master/JavaScript/JavaScript%E6%B7%B1%E5%85%A5%E4%B9%8B%E5%8E%9F%E5%9E%8B%E4%B8%8E%E5%8E%9F%E5%9E%8B%E9%93%BE.md'
        }
      ]
    }
  },
  methods: {
    goto (url){
      location.href= url
    }
  }
}
</script>

<style lang="less" scoped>
.five {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-image: linear-gradient(to top, #c1dfc4 0%, #deecdd 100%);
  flex-wrap: wrap;
  color: rgb(86, 98, 112);
  .header {
    margin-top: 45px;
    .header-text {
      font-size: 45px;
      text-align: center;
    }
  }
  .articleList {
    display: flex;
    justify-content: center;
    width: 100%;
    .article {
      display: flex;
      justify-content: space-around;
      flex-wrap: wrap;
      width: 85%;
      margin-top: 40px;
      .list {
        transition: all 1s;
        background: white;
        width: 43%;
        padding: 0px 20px 15px 20px;
        height: 150px;
        border-radius: 8px;
        box-shadow: 0px 1px 8px rgb(114, 114, 114);
        margin-bottom: 20px;
        .title {
          font-weight: bold;
          font-size: 25px;
          line-height: 50px;
          border-bottom: 1px dashed transparent;
          background: linear-gradient(white, white) padding-box,
            repeating-linear-gradient(
              -45deg,
              #ccc 0,
              #ccc 0.25em,
              white 0,
              white 0.75em
            );
        }
        .text {
          line-height: 26px;
          height: 80px;
          overflow: hidden;
          display: -webkit-box;
          -webkit-box-orient: vertical;
          -webkit-line-clamp: 3;
        }
        .time {
          display: flex;
          align-items: center;
          span {
            line-height: 25px;
            padding-left: 10px;
          }
          img {
            width: 20px;
            height: 20px;
          }
        }
      }
      .list:hover {
        box-shadow: 0px 5px 15px rgb(114, 114, 114);
      }
    }
  }
}
</style>