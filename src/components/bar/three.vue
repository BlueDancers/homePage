<template>
  <div class="three">
    <div class="header">
      <div class="header-text">
        <p>我的技能</p>
      </div>
    </div>
    <div class="main">
      <div class="cardlist">
        <div class="list" v-for="(item,index) in cards" :key="index">
          <div class="isShowText">
            <p>{{ item.text }}</p> 
          </div>
          <div class="list-img" @mouseleave="mouseleaves">
            <img :src="item.img" alt="">
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
      cards: [
        {
          img: '../../../static/three/html.png',
          text: 'HTML'
        },
        {
          img: '../../../static/three/css3.png',
          text: 'CSS3'
        },
        {
          img: '../../../static/three/javascript.png',
          text: 'JavaScript,ES6'
        },
        {
          img: '../../../static/three/java.png',
          text: 'Java,JavaWeb'
        },
        {
          img: '../../../static/three/wecart.jpg',
          text: '微信小程序'
        },
        {
          img: '../../../static/three/node.svg',
          text: 'Node.js'
        },
        {
          img: '../../../static/three/database.png',
          text: 'mysql,mongoDB'
        },
        {
          img: '../../../static/three/docker.png',
          text: 'Docker'
        }
      ]
    }
  },
  methods: {
    mouseleaves() {
      console.log('鼠标离开了')
    }
  }
}
</script>

<style lang="less" scoped>
.three {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-image: linear-gradient(to top, #37ecba 0%, #72afd3 100%);
  flex-wrap: wrap;
  color: white;
  .header {
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 50px 0px;
    .header-text {
      p {
        font-size: 45px;
      }
    }
  }
  .main {
    width: 100%;
    display: flex;
    justify-content: center;
    @media screen and (min-width: 950px) {
      .cardlist {
        //基本图标主题布局设置
        width: 80%;
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
        .list {
          .list-img {
            margin: 30px 50px;
            background-color: white;
            box-shadow: 0 3px 10px rgb(97, 95, 95);
            transition: all 0.5s;
            //每一个布局设置
            border-radius: 50%;
            width: 180px;
            height: 180px;
            text-align: center;
            line-height: 180px;
            img {
              width: 130px;
            }
          }
        }
        .list:nth-child(1) {
          .list-img {
            background-color: white;
          }
        }
        .list:nth-child(2) {
          .list-img {
            background-color: white;
          }
        }
        .list:nth-child(3) {
          .list-img {
            background-color: yellow;
            img {
              width: 150px;
            }
          }
        }
        .list:nth-child(4) {
          .list-img {
            background-color: rgb(46, 60, 70);
            img {
              width: 100px;
            }
          }
        }
        .list:nth-child(5) {
          .list-img {
            background-color: white;
            img {
              position: relative;
              bottom: 1px;
              border-radius: 50%;
              width: 180px;
            }
          }
        }
        .list:nth-child(6) {
          .list-img {
            background-color: rgb(51, 51, 51);
          }
        }
        .list:nth-child(7) {
          .list-img {
            background-color: rgb(229, 235, 245);
          }
        }
        .list:nth-child(8) {
          .list-img {
            background-color: rgb(228, 245, 255);
          }
        }
        .isShowText {
          position: relative;
          bottom: -50px;
          text-align: center;
          padding: 0 30px;
          opacity: 0;
          transition: all 0.5s;
          transition-timing-function: ease-out;
          p {
            line-height: 40px;
            border-radius: 5px;
            color: rgb(86, 98, 112);
            background-color: white;
            box-shadow: 0px 2px 5px rgb(97, 95, 95);
          }
        }

        .list:hover .isShowText {
          //animation: isShow .3s ease-in 0s 1 normal forwards;
          opacity: 1;
          position: relative;
          bottom: 1px;
        }
        .list-img:hover {
          box-shadow: 0 5px 20px rgb(92, 90, 90);
        }
      }
    }
    @media screen and (max-width: 950px) {
      .cardlist {
        //基本图标主题布局设置
        position: relative;
        bottom: 40px;
        width: 80%;
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
        .list {
          .list-img {
            margin: 10px 25px;
            background-color: white;
            box-shadow: 0 3px 10px rgb(97, 95, 95);
            transition: all 0.5s;
            //每一个布局设置
            border-radius: 50%;
            width: 90px;
            height: 90px;
            text-align: center;
            line-height: 90px;
            img {
              width: 50px;
            }
          }
        }
        .list:nth-child(1) {
          .list-img {
            background-color: white;
          }
        }
        .list:nth-child(2) {
          .list-img {
            background-color: white;
          }
        }
        .list:nth-child(3) {
          .list-img {
            background-color: yellow;
            img {
              width: 80px;
            }
          }
        }
        .list:nth-child(4) {
          .list-img {
            background-color: rgb(46, 60, 70);
            img {
              width: 40px;
            }
          }
        }
        .list:nth-child(5) {
          .list-img {
            background-color: white;
            img {
              position: relative;
              bottom: 1px;
              border-radius: 50%;
              width: 90px;
            }
          }
        }
        .list:nth-child(6) {
          .list-img {
            background-color: rgb(51, 51, 51);
          }
        }
        .list:nth-child(7) {
          .list-img {
            background-color: rgb(229, 235, 245);
          }
          .isShowText {
            p {
              font-size: 12px;
            }
          }
        }
        .list:nth-child(8) {
          .list-img {
            background-color: rgb(228, 245, 255);
          }
        }
        .isShowText {
          position: relative;
          bottom: -50px;
          text-align: center;
          opacity: 0;
          transition: all 0.5s;
          transition-timing-function: ease-out;
          p {
            line-height: 20px;
            border-radius: 5px;
            color: black;
            background-color: white;
            box-shadow: 0px 2px 5px rgb(97, 95, 95);
          }
        }

        .list:hover .isShowText {
          //animation: isShow .3s ease-in 0s 1 normal forwards;
          opacity: 1;
          position: relative;
          bottom: 0px;
        }
        .list-img:hover {
          box-shadow: 0 5px 20px rgb(92, 90, 90);
        }
      }
    }
    @media screen and (max-width: 320px) {
      .cardlist {
        //基本图标主题布局设置
        position: relative;
        bottom: 50px;
        width: 80%;
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
        .list {
          .list-img {
            margin: 5px 20px;
            background-color: white;
            box-shadow: 0 3px 10px rgb(97, 95, 95);
            transition: all 0.5s;
            //每一个布局设置
            border-radius: 50%;
            width: 80px;
            height: 80px;
            text-align: center;
            line-height: 80px;
            img {
              width: 50px;
            }
          }
        }
        .list:nth-child(1) {
          .list-img {
            background-color: white;
          }
        }
        .list:nth-child(2) {
          .list-img {
            background-color: white;
          }
        }
        .list:nth-child(3) {
          .list-img {
            background-color: yellow;
            img {
              width: 75px;
            }
          }
        }
        .list:nth-child(4) {
          .list-img {
            background-color: rgb(46, 60, 70);
            img {
              width: 40px;
            }
          }
        }
        .list:nth-child(5) {
          .list-img {
            background-color: white;
            img {
              position: relative;
              bottom: 1px;
              border-radius: 50%;
              width: 80px;
            }
          }
        }
        .list:nth-child(6) {
          .list-img {
            background-color: rgb(51, 51, 51);
          }
        }
        .list:nth-child(7) {
          .list-img {
            background-color: rgb(229, 235, 245);
          }
          .isShowText {
            p {
              font-size: 12px;
            }
          }
        }
        .list:nth-child(8) {
          .list-img {
            background-color: rgb(228, 245, 255);
          }
        }
        .isShowText {
          position: relative;
          bottom: -40px;
          text-align: center;
          opacity: 0;
          transition: all 0.5s;
          transition-timing-function: ease-out;
          p {
            line-height: 20px;
            border-radius: 5px;
            color: black;
            background-color: white;
            box-shadow: 0px 2px 5px rgb(97, 95, 95);
          }
        }

        .list:hover .isShowText {
          //animation: isShow .3s ease-in 0s 1 normal forwards;
          opacity: 1;
          position: relative;
        }
        .list-img:hover {
          box-shadow: 0 5px 20px rgb(92, 90, 90);
        }
      }
    }
  }
}
</style>