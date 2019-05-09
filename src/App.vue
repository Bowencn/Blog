<template>
  <div id="app">
    <!-- <div class="background">
      <img :src="backImg" class=".img-responsive">
    </div> -->
    
    <div class="topbck">
      <nav></nav>
      <span class="navbtn" @click="show = !show"></span>
      <div class="blog">
        <h1>bw's Blog</h1>
        <p>Do it!</p>
      </div>
    </div>
    <div class="content">
      <div class="box">
        <div class="main">
          <div class="aboutMe">
            <h1>About me</h1>
            <p>学习&项目&成长经历：</p>
          </div>
          <ul class="list">
            <div v-for="item in items.years" :key="item.id" class="container">
              <h3>{{item.year}}</h3>
              <li v-for="data in item.data" :key="data.id">
                <span class="date">{{data.date}}</span>
                <p>{{data.title}}</p>
              </li>
            </div>
          </ul>
        </div>
        <div class="log">log</div>
        <!-- <div class="left"></div>
        <div class="end"></div> -->
      </div>
      <footer class="footer">
        <p>©2019 - 2019 By bw</p>
      </footer>
    </div>
    
    <transition name="slide-fade">
      <slideBar class="Sidebar" v-show="show"></slideBar>
    </transition>
  </div>
</template>

<script>
import backgroundImg from "./assets/18.jpg";
import slideBar from "./components/slideBar";
export default {
  name: 'app',
  data(){
    return{
      backImg:backgroundImg,
      show:false,
      items:{
        years:{
          '2018':{
            year:'2018',
            data:{
              '180516':{
                date:'05-16',
                title:'于18年5月入坑前端，学习html、css知识并写出淘宝首页静态页面 【Html+Css】'
              },
              '180612':{
                date:'06-12',
                title:'开始学习jQuery，开发轮播图插件 【Css+jQuery】'
              },
              '180704':{
                date:'07-04',
                title:'进一步学习jQuery，仿写豆瓣音乐 【Html+Css+jQuery】'
              },
              '180820':{
                date:'08-20',
                title:'尝试使用gulp打包工具，结合之前所学知识开发QQ音乐播放页面 【Html+Css+jQuery+gulp】'
              },
              '181009':{
                date:'10-09',
                title:'初次接触Bootstrap 尝试使用并简单写了一个博客主页 【Html+Css+Bootstrap】'
              },
              '181119':{
                date:'11-19',
                title:'简单尝试微信小程序 【小程序】'
              },
              '181127':{
                date:'11-27',
                title:'开始接触Vue 仿写饿了么 【Vue】'
              }
            }
          },
          '2019':{
            year:'2019',
            data:{
              '190206':{
                date:'02-06',
                title:'用卷小程序 【小程序】'
              },
              '190227':{
                date:'02-27',
                title:'Vue开发书城（移动端） 【Vue】'
              },
              '190329':{
                date:'03-29',
                title:'开坑知乎日报 【Vue全家桶】'
              },
              '190426':{
                date:'04-26',
                title:'开发博客 【Vue】'
              }
            }
          }
        }
      }
    }
  },
  components:{
    slideBar:slideBar
  },
  mounted(){
    this.box()
  },
  methods:{
    box:function () {
      var box = document.querySelector(".box"),
          downX, downY, moveX, moveY, tempX, tempY, degX = 0, degY = 0;
      window.onmousedown = function (e) {
        e = e || event;
        downX = e.clientX;			//获取鼠标点下去时的坐标
        downY = e.clientY;
        window.onmousemove = function (e) {
          e = e || event;
          moveX = e.clientX - downX;			//算出鼠标移动的距离
              //根据一定比例将变化反应在盒子上，改变比例5可以调节拖动的速度
          tempX = degX + moveX / 5;
          tempY = 0;
          if (tempX>0) {
            tempX = 0
          }else if(tempX < -90){
            tempX = -90
          }
          box.style.transform = "rotatex(" + tempY + "deg) rotatey(" + tempX + "deg)";
        };
      };
      window.onmouseup = function (e) {
          e = e || event;
          if (tempX<=-45) {
            box.style.transform = "rotatex(" + tempY + "deg) rotatey(" + -90 + "deg)"
          }else if(tempX > -45){
            box.style.transform = "rotatex(" + tempY + "deg) rotatey(" + 0 + "deg)"
          }
          degX += moveX / 5;			//鼠标松开时将拖动期间改变的最终结果保存
          degY += - moveY / 5;
          window.onmousemove = null;			//取消监听
      };
    }
  }
}
</script>

<style lang="scss">
@import url('./assets/reset.css');
html{
  height: 100%;
  &::-webkit-scrollbar { width: 0 !important }
  body{
    height: 100%;
    text-align: center;
    min-width: 1000px;
    // background: url('./assets/b1.jpg');
    // background-color: #FEDFE1;
      #app{
        height: 100%;
        width: 100%;
        // position: relative;
        .topbck{
            background-image: url('./assets/b1.jpg');
            width: 100%;
            height: 30vw;
            background-size: 100%;
            background-position-y: 40vw;
            position: relative;
            .navbtn{
              background-image: url('./assets/导航.png');
              position: absolute;
              background-size: 100%;
              height: 1.5vw;
              width: 1.5vw;
              opacity: 0.3;
              top: 1vw;
              right: 1vw;
              z-index: 99;
              transition: all 0.4s ease-in-out;
              &:hover{
                opacity: 0.8;
                transform: rotate(360deg) scale(1.2)
              }
            }
            .blog{
              color: #fff;
              position: absolute;
              top: 50%;
              left: 50%;
              transform: translate(-50%,-50%);
              h1{
                font-size: 50px;
                font-weight: 700;
              }
              p{
                font-size: 24px;
                padding-top: 1vw;
              }
            }
          }
          .content{
            background-color: rgba(255,255,255,1);
            width: 100%;
            user-select: none;
            height: 100%;
            position: relative;
            .box{
              width: 60vw;
              position: relative;
              transform-style: preserve-3d;
              height: 100%;
              margin: 5vw auto 0;
              // .left{
              //   width: 60vw;
              //   // height: 100%;
              //   // box-shadow: 1px 1px 5px 1px rgb(119, 119, 119);
              //   margin: 5vh auto 0;
              //   transform: rotateY(-90deg) rotateX(0deg) translateZ(30vw)
              // }
              // .end{
              //   width: 60vw;
              //   // height: 100%;
              //   // box-shadow: 1px 1px 5px 1px rgb(119, 119, 119);
              //   margin: 5vh auto 0;
              //   transform: rotateY(180deg) rotateX(0deg) translateZ(30vw)
              // }
              .log{
                width: 60vw;
                height: 100%;
                box-shadow: 1px 1px 5px 1px rgb(119, 119, 119);
                position: absolute;
                width: 100%;
                height: 100%;
                top: 0;
                left: 0;
                transform: rotateY(90deg) rotateX(0deg) translateZ(30vw)
              }
              .main{
                width: 60vw;
                height: 100%;
                box-shadow: 1px 1px 5px 1px rgb(119, 119, 119);
                position: absolute;
                width: 100%;
                height: 100%;
                top: 0;
                left: 0;
                transform: translateZ(30vw);
                display: flex;
                flex-direction: column;
                .aboutMe{
                  display: inline-block;
                  width: 100%;
                  text-align: left;
                  padding: 2vw;
                  h1{
                    font-size: 30px;
                    line-height: 30px;
                    font-weight: 700;
                    color: #005CAF;
                  }
                  p{
                    font-size: 17px;
                    font-weight: 600;
                    padding-top: 1vw;
                  }
                }
                .list{
                  width: 100%;
                  height: 100%;
                  text-align: left;
                  padding: 0 2vw 2vw;
                  display: inline-block;
                  .container{
                    padding: 0 2vw 2vw;
                    width: 100%;
                  }
                  h3{
                    font-size: 20px;
                    font-weight: 700;
                    color: #005CAF;
                  }
                  li{
                    font-size: 17px;
                    font-weight: 500;
                    padding: 2vw 3vw 0;
                    line-height: 20px;
                    width: 50vw;
                    .date{
                      font-weight: 700;
                      font-size: 18px;
                    }
                    p{
                      display: inline;
                      padding-left: 1vw;
                      letter-spacing: 1px;
                    }
                  }
                }
              }
            }
            .footer{
              width: 100%;
              height: 3vw;
              margin-top: 3vw;
              background-image: url('./assets/b1.jpg');
              width: 100%;
              background-size: 100%;
              background-position-y: 3vw;
              position: absolute;
              bottom: -2vw;
              p{
                position: absolute;
                top: 50%;
                left: 50%;
                transform: translate(-50%,-50%);
                color: #fff;
                font-size: 15px;
                font-weight: 700;
              }
            }
          }
        
        .slide-fade-enter-active{
          transition: all .7s ease;
        }
        .slide-fade-leave-active {
          transition: all .8s cubic-bezier(1.0, 0.5, 0.8, 1.0);
        }
        .slide-fade-enter, .slide-fade-leave-to
        /* .slide-fade-leave-active for below version 2.1.8 */ {
          transform: translateX(10px);
          opacity: 0;
        }
        .Sidebar{
          position: fixed;
          top: 10vw;
          right: 0;
          background-color: rgba(12, 12, 12, 0.7);
          box-shadow: 2px 4px 20px 2px rgba(0, 0, 0, 0.6);
          width: 5vw;
        }
    }
  }
}
</style>
