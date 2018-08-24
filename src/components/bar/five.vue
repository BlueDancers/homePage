<template>
  <div class="five">
    <div class="pages">
      <div class="header">
        <p>项目与作品</p>
      </div>



      <div class="card">
        <div class="card-list">
          <transition-group name="fade"> 
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
                  <img src="../../../static/five/查看.png">
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

      <div class="direction">
        <div class="direction-list">
          <div>
            <div class="direction-add">
              <img src="../../../static/five/左.png" alt="" @click="tablebar('add')">
            </div>
            <div class="direction-less">
              <img src="../../../static/five/右.png" alt=""  @click="tablebar('less')">
            </div>
          </div>
        </div>
       
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      show: 0,
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
        if (this.show == 2) {
          this.show = 0
        } else {
          this.show++
        }
      }
      if (status === 'less') {
        if (this.show == 0) {
          this.show = 2
        } else {
          this.show--
        }
      }
    },
    gotoGithub() {
      location.href = 'https://github.com/vkcyan'
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
  background-image: linear-gradient(15deg, #13547a 0%, #80d0c7 100%);
  color: white;
  display: flex;
  justify-content: center;
  .pages {
    width: 100%;
    @media screen and (min-width: 375px) {
      .header {
        margin-top: 15px;
        text-align: center;
        margin-bottom: 20px;
        p {
          font-size: 45px;
        }
      }
    }

    @media screen and (max-width: 375px) {
      .header {
        margin-top: 15px;
        text-align: center;
        margin-bottom: 20px;
        p {
          font-size: 30px;
        }
      }
    }
    .card {
      .card-list {
        @media screen and (min-width: 1000px) {
          .cards {
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
            width: 60%;
            height: 500px;
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
                margin: 10px 0;
                p {
                  font-size: 13px;
                  line-height: 25px;
                  overflow: hidden;
                  display: -webkit-box;
                  -webkit-box-orient: vertical;
                  -webkit-line-clamp: 2;
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
            width: 60%;
            height: 420px;
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
                margin: 10px 0;
                p {
                  font-size: 12px;
                  line-height: 20px;
                  overflow: hidden;
                  display: -webkit-box;
                  -webkit-box-orient: vertical;
                  -webkit-line-clamp: 2;
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
    @media screen and (max-width: 320px) {
      .gotoGithub {
        display: flex;
        justify-content: center;
        align-items: center;
        position: relative;
        top: 75%;
        button {
          display: inline-block;
          background-color: white;
          width: 100%;
          border: 0px;
          border-radius: 5px;
          width: 60%;
          max-width: 400px;
          font-size: 15px;
          padding: 3px 0px;
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

    .gotoGithub button:hover {
      box-shadow: 0px 2px 5px #a19d9d;
      color: black;
      border: 1px white solid;
      background-color: white;
    }
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
</style>