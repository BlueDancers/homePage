<template>
  <div class="two">
    <div class="page">
      <div class="header">
        <p>自我介绍</p>
      </div>
      <div class="main">
        <div class="main-selfIntroduction">
          <p class="selfIntroduction">前端工程师,balibalia</p>
        </div>
        <div class="main-relevant">
          <div class="relevant-flex">
            <div class="relevant-icon-text" v-for="(items,index) in information" :key="index">
              <div>
                <img :src="items.img" alt="">
              </div>
              <div>
                <p>{{ items.text }}</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <!--http://www.ahiib.com/75/a6/c188a30118/page.htm-->
  </div>
</template>

<script>
export default {
  data() {
    return {
      information: [
        {
          img: '../../../static/two/生日.png',
          text: '1998.11.30'
        },
        {
          img: '../../../static/two/大学.png',
          text: '专科 计算机应用'
        },
        {
          img: '../../../static/two/合肥.png',
          text: '安徽 合肥'
        },
        {
          img: '../../../static/two/手机.png',
          text: '173xxxx6635(安徽)'
        },
        {
          img: '../../../static/two/邮箱.png',
          text: 'wu.vkcyan@gmail.com'
        },
        {
          img: '../../../static/two/获奖.png',
          text: '先电云计算大赛全国一等奖'
        }
      ]
    }
  }
}
</script>

<style lang="less" scoped>
.two {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  //background-color: rgba(28, 120, 192);
  background-image: linear-gradient(to top, #1d235f 0%, #516395 100%);
  color: white;
  display: flex;
  justify-content: center;
  align-items: center;
  .page {
    position: relative;
    top: 10%;
    width: 100%;
    height: 100%;
    .header {
      display: flex;
      justify-content: center;
      font-size: 45px;
      padding-bottom: 40px;
    }
    .main {
      max-width: 100%;
      display: flex;
      flex-wrap: wrap; //折行
      justify-content: center;
      .main-selfIntroduction {
        width: 80%;
        max-width: 1300px;
        display: flex;
        justify-content: center;
        background-color: white;
        border-radius: 3px;
        box-shadow: 0px 3px 10px rgba(0, 0, 0, 0.1);
        .selfIntroduction {
          display: inline-block;
          line-height: 55px;
          color: black;
        }
        margin-bottom: 5%;
      }
      .main-relevant {
        width: 80%;
        max-width: 1300px;
        display: flex;
        justify-content: center;
        background-color: white;
        border-radius: 3px;
        box-shadow: 0px 3px 10px rgba(0, 0, 0, 0.1);
        @media screen and (min-width: 950px) {
          .relevant-flex {
            width: 70%;
            display: flex;
            justify-content: space-around;
            align-items: center;
            flex-wrap: wrap;
            .relevant-icon-text {
              width: 260px;
              margin: 20px 0;
              div {
                display: flex;
                justify-content: center;
                img {
                  width: 40px;
                  height: 40px;
                }
                p {
                  color: black;
                }
              }
            }
          }
        }
        @media screen and (max-width: 950px) {
          .relevant-flex {
            width: 100%;
            justify-content: flex-start;
            align-items: center;
            flex-wrap: wrap;
            .relevant-icon-text {
              display: flex;
              align-items: center;
              width: 100%;
              border-bottom: 1px solid #ebedee;
              margin: 10px 0px;
              div {
                display: flex;
                align-items: center;
                img {
                  width: 30px;
                  height: 30px;
                  margin: 0 10px;
                }
                p {
                  color: black;
                }
              }
            }
            .relevant-icon-text:last-child{   //最后一个清除下划线
              border-bottom: 0px solid #ebedee;
            }
          }
        }
      }
    }
  }
}
</style>