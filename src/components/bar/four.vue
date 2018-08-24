<template>
  <div class="four">
    <div class="four-page">
      <div class="leftpage">
        <div class="header">
          <p>技能清单</p> 
        </div>
        <div class="mainCover">   
          <div class="cover">
            <img src="../../../static/one/user.jpg" alt="">
            <p>有灵感再补</p>
          </div>
        </div>
        <div class="main">
          <div class="list-text">
            <div class="list" v-for="(item,index) in leftData" :key="index">
              <p class="text">
                {{ item.title }} : {{ item.text }}
              </p>
            </div>
          </div>
        </div>
      </div>
      <div class="rigthpage">
        <div class="header">
          <p>大体上目前开发技能的掌握程度如下所述</p>
        </div>
        <div class="main">
          <div class="list-text">
            <div class="list" v-for="(item,index) in rigthData" :key="index">
              <p class="text">
                ○ {{ item.text }}
              </p>
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
      leftData: [
        {
          title: 'Web开发',
          text: 'JavaScript / html5 / css3 / 小程序 /jquery'
        },
        {
          title: '前端框架',
          text: 'Vue / mpvue'
        },
        {
          title: 'UI框架',
          text: 'bootstrap / element-ui'
        },
        {
          title: '前端工具',
          text: ' webpack / rollup / Less / git'
        },
        {
          title: '数据库',
          text: 'mysql / mongdb'
        },
        {
          title: '后端开发',
          text: 'node.js / JavaEE'
        },
        {
          title: '后端框架',
          text: 'koa2 / SSH(Spring SpringMVC Hibernate)'
        },
        {
          title: '单元测试',
          text: 'JUnit'
        },
        {
          title: '运维',
          text: '了解linux / Jenkins / docker(Dockerfile compose rancherHA)'
        }
      ],
      rigthData: [
        {
          text:
            '(HTML) 熟悉HTML标签，理解Dom结构，了解HTML5，CSS3常用属性,flex布局'
        },
        {
          text:
            '(ES3) 掌握JavaScript基本知识，理解作用域，闭包，原型，原型链等基础知识'
        },
        {
          text: '(ES6) 熟悉ES6相关知识对es6的大致总结'
        },
        {
          text:
            '(Vue) 熟悉Vue以及Vue全家桶登录模块 购物车模块 商城系统后端开发中'
        },
        {
          text: '(JavaWeb) 了解javaWeb，开发参与过ssh的网盘系统'
        },
        {
          text: '(Native) 了解媒体查询，做过两个以上小程序项目'
        },
        {
          text:
            '(Node) 使用Node写过一些后端，熟悉koa2框架以及koa2的中间件编写方式'
        },
        {
          text:
            '(HTTP) 理解HTTP基础知识，常见响应吗http缓存等知识，理解RESTful API'
        },
        {
          text:
            '(Other) 了解Linux命令行操作，了解git版本控制，了解webpack/rollup基本配置'
        }
      ]
    }
  }
}
</script>

<style lang="less" scoped>
@media screen and (min-width: 750px) {
  .four {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-image: linear-gradient(
      -225deg,
      #473b7b 0%,
      #3584a7 51%,
      #30d2be 100%
    );
    display: flex;
    justify-content: center;
    align-items: center;
    .four-page {
      width: 90%; //整体是页面的80%
      height: 700px;
      min-height: 650px;
      display: flex; //定制css
      .leftpage {
        box-shadow: -5px 2px 20px 1px #4d4a4a; //左页
        z-index: 10; //覆盖右页
        border-top-left-radius: 10px;
        border-bottom-left-radius: 10px;
        animation: pagerotateleft 3s ease-in 0s 1 normal forwards;
        transform: translate3d(0, 0, 0);
        //性能优化
        -webkit-transform-style: preserve-3d;
        -webkit-transform-origin: right;
      }
      @keyframes pagerotateleft {
        0% {
          -webkit-transform: rotateY(180deg);
        }
        100% {
          -webkit-transform: rotateY(0deg);
        }
      }
      .rigthpage {
        //右页
        box-shadow: 2px 2px 20px 1px #4d4a4a;
        right: 5%;
        border-top-right-radius: 10px;
        border-bottom-right-radius: 10px;
        animation: pagerotateright 3s ease-in 0s 1 normal forwards;
        -webkit-transform-style: preserve-3d;
        -webkit-transform-origin: left;
      }
      @keyframes pagerotateright {
        from {
          -webkit-transform: rotateY(-0deg);
        }
        to {
          -webkit-transform: rotateY(0deg);
        }
      }
      //下面为公共css
      .rigthpage,
      .leftpage {
        height: 90%;
        position: absolute;
        color: black;
        background: white;
        width: 45%;
        .header {
          width: 80%;
          margin-top: 40px;
          display: inline-block;
          animation: showdappear 3s ease-in 0s normal forwards;
          p {
            font-size: 25px;
            position: relative;
            left: 30px;
            overflow: hidden;
            text-overflow: ellipsis;
            white-space: nowrap;
          }
        }
        .mainCover {
          position: absolute;
          animation: showdisappear 3s ease-in 0s normal forwards;
          width: 100%;
          height: 100%;
          bottom: 0;
          left: 0;
          .cover {
            position: absolute;
            left: 30%;
            top: 30%;
            width: 40%;
            height: 40%;
            text-align: center;
            line-height: 270px;
            img {
              width: 200px;
              height: 200px;
              border-radius: 50%;
            }
          }
        }
        .main {
          animation: showdappear 3s ease-in 0s normal forwards;
          height: 80%;
          display: flex;
          justify-content: center;
          .list-text {
            height: 80%;
            position: relative;
            top: 40px;
            width: 90%;
            color: rgb(86, 98, 112);
            border-radius: 3px;
            .list {
              border-bottom: 1px dashed transparent;
              background: linear-gradient(white, white) padding-box,
                repeating-linear-gradient(
                  -45deg,
                  #ccc 0,
                  #ccc 0.25em,
                  white 0,
                  white 0.75em
                );
              .text {
                position: relative;
                left: 20px;
                font-size: 16px;
                line-height: 55px;
                padding: 1em;
                overflow: hidden;
                text-overflow: ellipsis;
                white-space: nowrap;
              }
            }
            .list:first-child {
              border-top: 1px dashed transparent;
              background: linear-gradient(white, white) padding-box,
                repeating-linear-gradient(
                  -45deg,
                  #ccc 0,
                  #ccc 0.25em,
                  white 0,
                  white 0.75em
                );
            }
          }
        }
        @keyframes showdisappear {
          //消失
          0% {
            opacity: 1;
          }
          50% {
            opacity: 1;
          }
          65% {
            opacity: 0;
          }
          100% {
            opacity: 0;
          }
        }
        @keyframes showdappear {
          //出现
          0% {
            opacity: 0;
          }
          50% {
            opacity: 0;
          }
          100% {
            opacity: 1;
          }
        }
      }
    }
  }
}
@media screen and (max-width: 750px) and (min-width: 500px) {
  .four {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-image: linear-gradient(
      -225deg,
      #473b7b 0%,
      #3584a7 51%,
      #30d2be 100%
    );
    display: flex;
    justify-content: center;
    align-items: center;
    .four-page {
      width: 90%; //整体是页面的80%
      min-height: 650px;
      display: flex; //定制css
      justify-content: center;
      .rigthpage {
        display: none;
      } //下面为公共css
      .leftpage {
        box-shadow: 0px 2px 20px 1px #4d4a4a;
        //左页
        z-index: 10; //覆盖右页
        border-radius: 10px;
        color: black;
        background: white;
        width: 90%;
        .header {
          width: 80%;
          margin-top: 40px;
          display: inline-block;
          p {
            font-size: 25px;
            position: relative;
            left: 30px;
            overflow: hidden;
            text-overflow: ellipsis;
            white-space: nowrap;
          }
        }
        .mainCover {
          display: none;
        }
        .main {
          height: 80%;
          display: flex;
          justify-content: center;
          .list-text {
            height: 80%;
            position: relative;
            top: 40px;
            width: 90%;
            color: black;
            border-radius: 3px;
            .list {
              border-bottom: 1px dashed transparent;
              background: linear-gradient(white, white) padding-box,
                repeating-linear-gradient(
                  -45deg,
                  #ccc 0,
                  #ccc 0.25em,
                  white 0,
                  white 0.75em
                );
              .text {
                position: relative;
                left: 20px;
                font-size: 16px;
                line-height: 55px;
                padding: 1em;
                overflow: hidden;
                text-overflow: ellipsis;
                white-space: nowrap;
              }
            }
            .list:first-child {
              border-top: 1px dashed transparent;
              background: linear-gradient(white, white) padding-box,
                repeating-linear-gradient(
                  -45deg,
                  #ccc 0,
                  #ccc 0.25em,
                  white 0,
                  white 0.75em
                );
            }
          }
        }
      }
    }
  }
}
@media screen and (max-width: 500px) {
  .four {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-image: linear-gradient(
      -225deg,
      #473b7b 0%,
      #3584a7 51%,
      #30d2be 100%
    );
    display: flex;
    justify-content: center;
    align-items: center;
    .four-page {
      width: 90%; //整体是页面的80%
      height: 70%;
      display: flex; //定制css
      justify-content: center;
      min-height: 400px;
      .rigthpage {
        display: none;
      }
      //下面为公共css
      .leftpage {
        box-shadow: 0px 2px 20px 1px #4d4a4a;
        //左页
        z-index: 10; //覆盖右页
        border-radius: 10px;
        color: black;
        background: white;
        width: 95%;
        .header {
          width: 80%;
          margin-top: 20px;
          display: inline-block;
          p {
            font-size: 25px;
            position: relative;
            left: 30px;
          }
        }
        .mainCover {
          display: none;
        }
        .main {
          height: 100%;
          display: flex;
          justify-content: center;
          .list-text {
            height: 80%;
            position: relative;
            top: 20px;
            width: 90%;
            color: black;
            border-radius: 3px;
            .list {
              border-bottom: 1px dashed transparent;
              background: linear-gradient(white, white) padding-box,
                repeating-linear-gradient(
                  -45deg,
                  #ccc 0,
                  #ccc 0.25em,
                  white 0,
                  white 0.75em
                );
              .text {
                position: relative;
                left: 5px;
                font-size: 12px;
                line-height: 30px;
                overflow: hidden;
                text-overflow: ellipsis;
                white-space: nowrap;
              }
            }
            .list:first-child {
              border-top: 1px dashed transparent;
              background: linear-gradient(white, white) padding-box,
                repeating-linear-gradient(
                  -45deg,
                  #ccc 0,
                  #ccc 0.25em,
                  white 0,
                  white 0.75em
                );
            }
          }
        }
      }
    }
  }
}
</style>