<template>
  <div id="app">
    <!-- <div class="background">
      <img :src="backImg" class=".img-responsive">
    </div> -->
    <div class="topbck">
      <nav></nav>
      <div class="blog">
        <h1>Chrise's Blog</h1>
        <p>Do it!</p>
      </div>
    </div>
    <div class="content">
      <div class="main">
        <div class="aboutMe">
          <h1>About me</h1>
          <p>学习&项目&成长经历：</p>
        </div>
        <ul class="list">
          <h3>{{years}}</h3>
          <li v-for="item in items" :key="item.id">
            <span class="date">{{item.date}}</span>
            <p>{{item.title}}</p>
          </li>
        </ul>
      </div>
    </div>
    <footer></footer>
    <!-- <slideBar class="Sidebar"></slideBar> -->
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
      items:{
        a:{
          date:'03-24',
          title:'开坑vue-koa-demo项目的前端测试。同期写了一篇Jest 全栈测试的经验博客。【Jest】'
        },
        b:{
          date:'03-24',
          title:'协助解决实验室Vue项目里webpack的Hot Reload速度太慢的问题，做了个webpack的开发模式的插件webpack-dev-compile-optimize提升热重载速度（只在自己内部项目测试过），同期总结了一篇基于vue-cli项目的webpack构建优化文章。【webpack】'
        }
      },
      years:'2019年'
    }
  },
  components:{
    slideBar:slideBar
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
    // background: url('./assets/b1.jpg');
    // background-color: #FEDFE1;
      #app{
        height: 100%;
        width: 100%;
        position: relative;
        // .background{
        //   position: relative;
        //   font-size: 0;
        // }
        .topbck{
            background-image: url('./assets/b1.jpg');
            // opacity: 0.8;
            width: 100%;
            height: 50vh;
            background-size: 100%;
            background-position-y: 88vh;
            position: relative;
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
            // height: 100%;
            .main{
              width: 60vw;
              // height: 100%;
              box-shadow: 1px 1px 5px 1px rgb(119, 119, 119);
              margin: 5vh auto 0;
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
                width: 100%;
                text-align: left;
                padding: 0 2vw 2vw;
                h3{
                  font-size: 17px;
                  font-weight: 700;
                  color: #005CAF;
                }
                li{
                  font-size: 14px;
                  font-weight: 500;
                  padding: 2vw 3vw 0;
                  line-height: 20px;
                  .date{
                    font-weight: 700;
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
        .Sidebar{
          position: fixed;
          top: 20vh;
          background-color: rgba(12, 12, 12, 0.7);
          // border-right: 1px solid rgba(0, 0, 0, 0.5);
          box-shadow: 2px 4px 20px 2px rgba(0, 0, 0, 0.6);
          width: 10vh;
          // height: 100vh;
        }
    }
  }
}
</style>
