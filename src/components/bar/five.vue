<template>
  <div class="five" @mousewheel="handleScroll" @touchstart="touchstart" @touchend="touchend" @mousedown="mousedown" @mouseup="mouseup">
    <div class="pages">
      <div class="header">
        <p>项目与作品</p>
      </div>
      <div class="card">
        <div class="card-list">
          <transition-group :name="isfade">
          <div class="cards" v-for="(item, index) in list" :key="index" v-show="index == show">
              <div class="card-list-image">
                <img :src="item.img">
              </div>
              <div class="card-list-title">
                <p>{{ item.title }}</p>
              </div>
              <div class="card-list-text">
                <div class="text">
                  <p v-for="(item, indexs) in item.text" :key="indexs">
                    ○ {{ item }}
                  </p>
                </div>
              </div>
              <div class="card-list-button">
                <button>
                  <img src="../../../static/five/look.png">
                </button>
              </div>
          </div>
          </transition-group>
        </div>
      </div>


      <div class="gotoGithub">
        <button @click="gotoGithub">
          <img src="../../../static/one/github.png">
          <span >查看更多项目</span>
        </button>
      </div>
      <!-- pc端左右按钮 -->
      <div class="direction">
        <div class="direction-list">
          <div>
            <div class="direction-add" @click="tablebar('add')">
              <img src="../../../static/five/left.png" alt="">
            </div>
            <div class="direction-less" @click="tablebar('less')">
              <img src="../../../static/five/right.png" alt="">
            </div>
          </div>
        </div>
      </div>
      <!-- 移动端按钮 -->
      <div class="mobileButton" v-show="mobileButton">
          <img src="../../../static/five/jiantou.png" alt="">
      </div>
    </div>
  </div>
</template>

<script>
export default {
  mounted () {
    this.isfade = ''
  },
  data() {
    return {
      show: 0,          //控制卡片切换
      mousedownevent: 0,//鼠标/手指按下记录
      mouseupevent: 0,  //鼠标/手指松开记录
      isfade: '',       //切换动画
      mobileButton: true,
      list: [
        {
          img: '../../../static/five/mpvue.png',
          title: 'mpvue+ wafer2(koa2 + kenx)',
          text: [
            '使用腾讯提供的wafer2服务端SDK',
            '使用Promise对wx.request等原生API进行二次封装，对主页面的记录显示组件化开发实现类瀑布流',
            '书写页面进行对textarea进行优化,最大字数的实时显示输入 字数取消传统保存按钮退出即保存',
            '对用户登录页面计划进行个性化设置以及整体布局程序编写中'
          ]
        },
        {
          img: '../../../static/five/cloud.png',
          title: '分布式存储系统Swift + ssh框架 + jquery + bootstrap',
          text: [
            '负责模块: 新建 删除 重命名 删除 上传 删除 下载 文件分享 创建群组 视图切换等等',
            '参与前期项目分析，设置ui基本设计图数据库设计，完成前端主页面',
            '​创建群组代码的重构，参与网盘详情的代码的重构，使用deferred异步编程，让代码提速1倍'
          ]
        },
        {
          img: '../../../static/five/o2o.png',
          title: 'O2O商城',
          text: [
            '这是一个完整的商城小程序,使用原生语言开发,负责前端所有ui与逻辑,比如登录, 下单, 预约 ,购物车',
            '对用户信息,购物车数据等等进行localStorage存储,减小后端的压力,优化用户体验​等'
          ]
        }
      ]
    }
  },
  methods: {
    tablebar(status) {
      if (status === 'add') {
        this.isfade = "fade"
        if (this.show == 2) {
          this.show = 0
        } else {
          this.show++
        }
      }
      if (status === 'less') {
        this.isfade = "fades"
        if (this.show == 0) {
          this.show = 2
        } else {
          this.show--
        }
      }
    },
    gotoGithub() {
      location.href = 'https://github.com/vkcyan'
    },
    // 移动端手势事件
    touchstart(e) {
      this.mousedownevent = e.targetTouches[0].clientX
    },
    touchend(e) {
      this.mouseupevent = e.changedTouches[0].clientX

      let result = this.mouseupevent - this.mousedownevent

      if (result > 0 && result > 80) {
        this.tablebar('less')
      }
      if (result < 0 && result < -80) {
        this.tablebar('add')
      }
      this.mobileButton = false //只要切换了,就隐藏移动端箭头
    },
    // pc端手势事件
    mousedown (e) {
      this.mousedownevent = e.screenX
    },
    mouseup (e) {
      this.mouseupevent = e.screenX
      let mousedistance = this.mousedownevent - this.mouseupevent

      if (mousedistance > 40)  {
        this.tablebar('add')
      }
      if (mousedistance < -40 ) {
        this.tablebar('less')
      }
    },
    handleScroll (e) {
      this.deltay = e.deltaY || e
    }
  }
}
</script>

<style lang="less" scoped>
.five {
  user-select: none;
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-image: linear-gradient(15deg, #13547a 0%, #80d0c7 100%);
  color: white;
  display: flex;
  justify-content: center;
  .pages {
    width: 100%;
    @media screen and (min-width: 376px) {
      .header {
        margin-top: 15px;
        text-align: center;
        margin-bottom: 20px;
        p {
          font-size: 45px;
        }
      }
    }

    @media screen and (max-width: 376px) {
      .header {
        margin-top: 10px;
        text-align: center;
        p {
          font-size: 30px;
        }
      }
    }
    .card {
      .card-list {
        @media screen and (min-width: 1000px) {
          .cards {
            cursor:pointer;
            position: relative;
            box-shadow: 0px 2px 10px 4px #6d6868a6;
            background: white;
            border-radius: 10px;
            color: rgb(86, 98, 112);
            position: absolute;
            width: 60%;
            height: 550px;
            top: 13%;
            left: 20%;
            .card-list-image {
              margin-top: 10px;
              text-align: center;
              img {
                border-radius: 10px;
                width: 600px;
              }
            }
            .card-list-title {
              margin-top: 20px;
              p {
                text-align: center;
                font-size: 20px;
              }
            }
            .card-list-text {
              margin: 30px 0;
              display: flex;
              justify-content: center;
              .text {
                padding: 0 20px;
                width: 100%;
                p {
                  line-height: 25px;
                  overflow: hidden;
                  text-overflow: ellipsis;
                  white-space: nowrap;
                }
              }
            }
            .card-list-button {
              position: absolute;
              bottom: 8px;
              right: 3px;

              button {
                cursor:pointer;
                transition: all 0.5s;
                background-color: white;
                border: 1px solid #ffffff;
                border-radius: 4px;
                margin-right: 20px;
                img {
                  width: 30px;
                  height: 30px;
                }
              }
            }
            .card-list-button button:hover {
              border: 1px solid #000000;
            }
          }
        }
        @media screen and (max-width: 999px) and (min-width: 500px) {
          .cards {
            position: relative;
            box-shadow: 0px 2px 10px 4px #6d6868a6;
            background: white;
            border-radius: 10px;
            color: rgb(86, 98, 112);
            position: absolute;
            width: 60%;
            top: 13%;
            left: 20%;
            .card-list-image {
              margin-top: 40px;
              text-align: center;
              img {
                border-radius: 10px;
                width: 90%;
              }
            }
            .card-list-title {
              margin-top: 20px;
              p {
                text-align: center;
                font-size: 15px;
              }
            }
            .card-list-text {
              margin: 20px 0;
              display: flex;
              justify-content: center;
              .text {
                padding: 0 20px;
                width: 100%;
                p {
                  line-height: 25px;
                }
              }
            }
            .card-list-button {
              position: absolute;
              bottom: 8px;
              right: 3px;
              button {
                transition: all 0.5s;
                background-color: white;
                border: 1px solid #ffffff;
                border-radius: 4px;
                margin-right: 20px;
                img {
                  width: 30px;
                  height: 30px;
                }
              }
            }
            .card-list-button button:hover {
              border: 1px solid #000000;
            }
          }
        }
        @media screen and (max-width: 499px) and (min-width: 321px) {
          .cards {
            position: relative;
            box-shadow: 0px 2px 10px 2px #6d6868a6;
            background: white;
            border-radius: 8px;
            color: rgb(86, 98, 112);
            position: absolute;
            width: 80%;
            height: 420px;
            top: 13%;
            left: 10%;
            .card-list-image {
              margin-top: 40px;
              text-align: center;
              img {
                border-radius: 10px;
                width: 90%;
              }
            }
            .card-list-title {
              margin-top: 20px;
              p {
                text-align: center;
                font-size: 12px;
              }
            }
            .card-list-text {
              margin: 20px 10px;
              display: flex;
              justify-content: center;
              .text {
                padding: 0 20px;
                width: 100%;
                margin: 10px 0;
                p {
                  font-size: 13px;
                  line-height: 25px;
                  overflow: hidden;
                  text-overflow: ellipsis;
                  white-space: nowrap;
                }
              }
            }
            .card-list-button {
              position: absolute;
              bottom: 8px;
              right: 3px;
              button {
                transition: all 0.5s;
                background-color: white;
                border: 1px solid #ffffff;
                border-radius: 4px;
                margin-right: 20px;
                img {
                  width: 30px;
                  height: 30px;
                }
              }
            }
            .card-list-button button:hover {
              border: 1px solid #000000;
            }
          }
        }
        @media screen and (max-width: 320px) {
          .cards {
            position: relative;
            box-shadow: 0px 2px 10px 2px #6d6868a6;
            background: white;
            border-radius: 8px;
            color: rgb(86, 98, 112);
            position: absolute;
            width: 80%;
            height: 350px;
            top: 13%;
            left: 10%;
            .card-list-image {
              margin-top: 40px;
              text-align: center;
              img {
                border-radius: 10px;
                width: 90%;
              }
            }
            .card-list-title {
              margin-top: 20px;
              p {
                text-align: center;
                font-size: 15px;
              }
            }
            .card-list-text {
              margin: 20px 0;
              display: flex;
              justify-content: center;
              .text {
                padding: 0 20px;
                width: 100%;
                margin: 10px 0;
                p {
                  font-size: 12px;
                  line-height: 20px;
                  overflow: hidden;
                  display: -webkit-box;
                  -webkit-box-orient: vertical;
                  -webkit-line-clamp: 1;
                }
              }
            }
            .card-list-button {
              position: absolute;
              bottom: 8px;
              right: 3px;
              button {
                transition: all 0.5s;
                background-color: white;
                border: 1px solid #ffffff;
                border-radius: 4px;
                margin-right: 20px;
                img {
                  width: 30px;
                  height: 30px;
                }
              }
            }
            .card-list-button button:hover {
              border: 1px solid #000000;
            }
          }
        }
      }
    }
    .gotoGithub {
      display: flex;
      justify-content: center;
      align-items: center;
      position: relative;
      top: 580px;
      button {
        display: inline-block;
        background-color: white;
        width: 100%;
        border: 0px;
        border-radius: 5px;
        width: 400px;
        font-size: 15px;
        padding: 5px 0px;
        background-color: rgba(0, 0, 0, 0);
        transition: all 0.5s;
        box-shadow: 0px 0px 5px #6e6e6e;
        border: 1px white solid;
        color: rgb(255, 255, 255);
        img {
          width: 30px;
          height: 30px;
        }
        span {
          padding-left: 5px;
        }
      }
    }

    @media screen and (max-width: 999px) and (min-width: 500px) {
      .gotoGithub {
        display: flex;
        justify-content: center;
        align-items: center;
        position: relative;
        top: 78%;
        button {
          display: inline-block;
          background-color: white;
          width: 100%;
          border: 0px;
          border-radius: 5px;
          width: 60%;
          max-width: 400px;
          font-size: 15px;
          padding: 5px 0px;
          background-color: rgba(0, 0, 0, 0);
          transition: all 0.5s;
          box-shadow: 0px 0px 5px #6e6e6e;
          border: 1px white solid;
          color: rgb(255, 255, 255);
          img {
            width: 30px;
            height: 30px;
          }
          span {
            padding-left: 5px;
          }
        }
      }
    }
    @media screen and (max-width: 499px) {
      .gotoGithub {
        display: none;
      }
    }
    @media screen and (max-width: 320px) {
      .gotoGithub {
        display: none;
      }
    }

    .gotoGithub button:hover {
      box-shadow: 0px 2px 5px #a19d9d;
      color: black;
      border: 1px white solid;
      background-color: white;
    }
    @media screen and (max-width: 499px) {
      .direction {
        display: none;
      }
      .mobileButton {
        position: absolute;
        top: 450px;
        left: 150px;
        animation: movingArrow 2s linear 0s infinite normal none;
        img {
          width: 40px;
          height: 40px;
        }
      }
      @keyframes movingArrow {
        0% {
          left: 140px;
        }
        50% {
          left: 160px;
        }
        100% {
          left: 140px;
        }
      }
    }
    @media screen and (min-width: 500px) {
      .direction {
        position: absolute;
        width: 100%;
        bottom: 47%;
        .direction-list {
          display: flex;
          justify-content: center;
          div {
            display: flex;
            justify-content: space-between;
            width: 92%;
            transition: all 1s;
            .direction-add {
              img {
                transition: all 0.5s;
                height: 50px;
              }
            }
            .direction-less {
              position: relative;
              left: 10px;
              img {
                transition: all 0.5s;
                position: absolute;
                right: 0px;
                height: 50px;
              }
            }
          }
        }
      }
      .mobileButton {
        display: none
      }
    }

    .direction-add img:hover {
      padding-left: 10px;
    }
    .direction-less img:hover {
      padding-right: 10px;
    }
  }
}

//动画
.fade-enter-active,
.fade-leave-active {
  transition: all 1s;
}
.fade-enter {
  transform: translateX(1100px);
}
.fade-leave-to {
  transform: translateX(-1100px);
}
.fades-enter-active,
.fades-leave-active {
  transition: all 1s;
}
.fades-enter {
  transform: translateX(-1100px);
  opacity: 0;
}
.fades-leave-to {
  transform: translateX(1100px);
  opacity: 0;
}
</style>
