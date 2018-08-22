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
                  <img src="../../../static/four/查看.png">
                </button>
              </div>
          </div>
          </transition-group>
        </div>
      </div>


      <div class="gotoGithub">
        <button>
          <img src="../../../static/one/github.png">
          <span>查看更多项目</span>
        </button>
      </div>

      <div class="direction">
        <div class="direction-list">
          <div>
            <img src="../../../static/four/左.png" alt="" @click="tablebar('add')">
            <img src="../../../static/four/右.png" alt=""  @click="tablebar('less')">
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
          img:
            'https://camo.githubusercontent.com/2245259c035d368dbf529611cf9be84a7caa501e/687474703a2f2f6f6e377230747167752e626b742e636c6f7564646e2e636f6d2f467539447932516a337a66716f692d48766b694c5649727945666a6f2e504e47',
          title: 'mpvue+ wafer2(koa2 + kenx)',
          text: [
            '使用腾讯提供的wafer2服务端SDK',
            '使用Promise对wx.request等原生API进行二次封装，对主页面的记录显示组件化开发实现类瀑布流',
            '书写页面进行对textarea进行优化,最大字数的实时显示输入 字数取消传统保存按钮退出即保存',
            '对用户登录页面计划进行个性化设置以及整体布局程序编写中'
          ]
        },
        {
          img:
            'http://on7r0tqgu.bkt.clouddn.com/Fly66cSnGMgq7REs4-P4ZLzIw8pH.png',
          title: '分布式储存系统Swift + ssh框架 + jquery + bootstrap',
          text: [
            '负责模块: 新建 删除 重命名 删除 上传 删除 下载 文件分享 创建群组 视图切换等等',
            '参与前期项目分析，设置ui基本设计图数据库设计，完成前端主页面',
            '​创建群组代码的重构，参与网盘详情的代码的重构，使用deferred异步编程，让代码提速1倍'
          ]
        },
        {
          img:
            'https://camo.githubusercontent.com/2245259c035d368dbf529611cf9be84a7caa501e/687474703a2f2f6f6e377230747167752e626b742e636c6f7564646e2e636f6d2f467539447932516a337a66716f692d48766b694c5649727945666a6f2e504e47',
          title: '原生小程序',
          text: [
            '小程序ui设计 项目需求分析使用的的原生的语言进行开发',
            '​ 完成 登录 下单 购物车 预约 等等'
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
    .header {
      margin-top: 15px;
      text-align: center;
      margin-bottom: 20px;
      p {
        font-size: 45px;
      }
    }
    .card {
      .card-list {
        .cards {
          box-shadow: 0px 2px 10px 4px #6d6868a6;
          background: white;
          border-radius: 10px;
          color: black;
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
              width: 450px;
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
            display: flex;
            justify-content: flex-end;
            button {
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
        }
      }
    }
    .gotoGithub {
      display: flex;
      justify-content: center;
      position: relative;
      top: 580px;
      button {
        background-color: white;
        width: 100%;
        border: 0px;
        border-radius: 5px;
        width: 400px;
        line-height: 40px;
        img {
          width: 30px;
          height: 30px;
        }
      }
    }
    .direction {
      position: absolute;
      width: 100%;
      bottom: 5%;
      .direction-list {
        display: flex;
        justify-content: center;
        div {
          display: flex;
          justify-content: space-between;
          width: 90%;
          img {
            height: 50px;
          }
        }
      }
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