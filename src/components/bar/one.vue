<template>
  <div class="one" @mousewheel="handleScroll">
    <div class="main">
      <div class="main_photo_text">
        <div class="main_photo">
          <div class="photo">
            <img src="../../../static/one/user.jpg" alt=" ">
          </div>

        </div>
        <div class="main_text">
          <p class="main_text_name">vkcyan</p>
          <p class="main_text_Introduction">前端新人,请多指教</p>
        </div>
      </div>
      <div class="main_img">
        <img v-for="(item,index) in imgs" :key="index" :src="item.img" alt="" @click="gotoLocation(item.address)">
      </div>
      <div class="gotoresume" v-show="resume" @click="gotoresume">
        <div>
          <img src="../../../static/one/resume.png" alt="" srcset="">
          <span>文字简历</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      resume: false,
      imgs: [
        {
          img: '../../../static/one/github.png',
          address: 'https://github.com/vkcyan'
        },
        {
          img: '../../../static/one/blog.png',
          address: 'https://vkcyan.github.io/'
        },
        {
          img: '../../../static/one/bokeyuan.png',
          address: 'https://www.cnblogs.com/wuvkcyan/'
        },
        {
          img: '../../../static/one/zhihu.png',
          address:
            'https://www.zhihu.com/people/zhang-zui-zhang-zui-zuo-zuo-zuo-zuo-zuo/activities'
        }
      ]
    }
  },
  methods: {
    gotoLocation(e) {
      location.href = e
    },
    gotoresume () {
      location.href = 'https://vkcyan.github.io/about/'
    },
    handleScroll () {
      this.resume = true
    }
  }
}
</script>

<style lang="less" scoped>
@media screen and (min-width: 600px) {
  .one {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-image: linear-gradient(120deg, #fdfbfb 0%, #ebedee 100%);
    display: flex;
    justify-content: center;
    align-items: center;
    color: white;
    .main {
      position: relative;
      bottom: 20%;
      .main_photo_text {
        .main_photo {
          display: flex;
          justify-content: center;
          width: 100%;
          height: 140px;
          .photo {
            width: 140px;
            height: 140px;
            padding: 0 3px 3px 3px;
            box-shadow: 0 5px 10px rgba(0, 0, 0, 0.1);
            border-radius: 50%;
            opacity: 0;
            animation: emerge 1s ease-in 0.5s 1 normal forwards;
            @keyframes emerge {
              from {
                opacity: 0;
              }
              to {
                opacity: 1;
              }
            }
            img {
              width: 140px;
              border-radius: 50%;
              animation: changehovertree 6s linear infinite normal;
              //animation: 绑定的想着器的keyframe的名称 动画时间 动画曲线  infinite无限播放 normal默认值为正向旋转
            }
          }

          @keyframes changehovertree {
            0% {
              transform: rotate(0);
            }
            50% {
              transform: rotate(180deg);
            }
            100% {
              transform: rotate(360deg);
            }
          }
        }
        .main_text {
          .main_text_name {
            color: #444;
            font-size: 30px;
            display: flex;
            justify-content: center;
            align-items: center;
            margin: 20px;
            line-height: 60px;
            opacity: 0;
            animation: imgemerge 1.5s ease-in 0.3s 1 normal forwards;
          }
          .main_text_Introduction {
            opacity: 0;
            font-size: 15px;
            display: flex;
            justify-content: center;
            color: #999;
            line-height: 50px;
            animation: imgemerge 1.5s ease-in 0.5s 1 normal forwards;
          }
        }
      }
      .main_img {
        opacity: 0;
        animation: imgemerge 1.5s ease-in 0.5s 1 normal forwards;
        @keyframes imgemerge {
          from {
            opacity: 0;
          }
          to {
            opacity: 1;
          }
        }
        img {
          width: 35px;
          margin:20px;
          cursor: pointer;
        }
        img:nth-child(3) {
          width: 50px;
        }
      }
    }
  }
}
@media screen and (max-width: 599px) {
  .one {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-image: linear-gradient(120deg, #fdfbfb 0%, #ebedee 100%);
    display: flex;
    justify-content: center;
    align-items: center;
    color: white;
    .main {
      position: relative;
      bottom: 10%;
      .main_photo_text {
        .main_photo {
          display: flex;
          justify-content: center;
          width: 100%;
          height: 140px;
          .photo {
            width: 140px;
            height: 140px;
            padding: 0 3px 3px 3px;
            box-shadow: 0 5px 10px rgba(0, 0, 0, 0.1);
            border-radius: 50%;
            opacity: 0;
            animation: emerge 1.5s ease-in 0.5s 1 normal forwards;
            @keyframes emerge {
              from {
                opacity: 0;
              }
              to {
                opacity: 1;
              }
            }
            img {
              width: 140px;
              border-radius: 50%;
              animation: changehovertree 6s linear infinite normal;
              //animation: 绑定的想着器的keyframe的名称 动画时间 动画曲线  infinite无限播放 normal默认值为正向旋转
            }
          }

          @keyframes changehovertree {
            0% {
              transform: rotate(0);
            }
            50% {
              transform: rotate(180deg);
            }
            100% {
              transform: rotate(360deg);
            }
          }
        }
        .main_text {
          .main_text_name {
            color: #444;
            font-size: 30px;
            display: flex;
            justify-content: center;
            align-items: center;
            margin: 20px;
            line-height: 60px;
            opacity: 0;
            animation: emerge 1.5s ease-in 0.5s 1 normal forwards;
          }
          .main_text_Introduction {
            font-size: 15px;
            display: flex;
            justify-content: center;
            color: #999;
            line-height: 50px;
          }
        }
      }
      .main_img {
        opacity: 0;
        animation: imgemerge 0.8s ease-in 0.2s 1 normal forwards;
        @keyframes imgemerge {
          from {
            opacity: 0;
          }
          to {
            opacity: 1;
          }
        }
        img {
          width: 35px;
          margin: 0 20px;
          margin: 20px;
          cursor: pointer;
        }
        img:nth-child(3) {
          width: 50px;
        }
      }
    }
  }
}
.gotoresume {
  opacity: 0;
  transition: all 0.5s;
  cursor: pointer;
  box-shadow: 1px 1px 0px rgb(238, 236, 236);
  animation: resume 2.5s ease-in 0.5s 1 normal forwards;
  display: flex;
  justify-content: center;
  border: 1px solid rgb(83, 82, 82);
  border-radius: 5px;
  div {
    img {
      width: 30px;
    }
    span {
      transition: all 0.5s;
      color: #999;
    }
  }
}
.gotoresume:hover {
  box-shadow: 1px 2px 3px #999;
  background: white;
  border: 1px solid rgb(211, 205, 205);
  span {
    color: black;
  }
}
@keyframes resume {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
</style>
