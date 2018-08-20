<template>
  <div class="one">
    <div class="main">
      <div class="main_photo_text">
        <div class="main_photo">
          <div class="photo">
            <img src="../../../static/user.jpg" alt=" ">
          </div>
          
        </div>
        <div class="main_text">
          <p class="main_text_name">vkcyan</p>
          <p class="main_text_Introduction">前端新人,请多指教</p>
        </div>
      </div>
      <div class="main_text">
        <img v-for="(item,index) in imgs" :key="index" :src="item.img" alt="" @click="gotoLocation(item.address)">
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      imgs: [
        {
          img: '../../../static/github.png',
          address: 'https://github.com/vkcyan'
        },
        {
          img: '../../../static/blog.png',
          address: 'https://vkcyan.github.io/'
        },
        {
          img: '../../../static/博客园.png',
          address: 'https://www.cnblogs.com/wuvkcyan/'
        },
        {
          img: '../../../static/知乎.png',
          address: 'https://www.zhihu.com/people/zhang-zui-zhang-zui-zuo-zuo-zuo-zuo-zuo/activities'
        }
      ]
    }
  },
  methods: {
    gotoLocation(e) {
      location.href = e
    }
  }
}
</script>

<style lang="less" scoped>
.one {
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
    .main_text {
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
        margin-top: 20px;
        cursor: pointer;
      }
      img:nth-child(3) {
        width: 50px;
      }
    }
  }
}
</style>
