<template>
  <div id="app">
    <!-- <div class="background">
      <img :src="backImg" class=".img-responsive">
    </div> -->
    <div class="main">
      <div class="content">
        
      </div>
    </div>
    <slideBar class="Sidebar"></slideBar>
  </div>
</template>

<script>
import backgroundImg from "./assets/18.jpg";
import slideBar from "./components/slideBar";
export default {
  name: 'app',
  data(){
    return{
      backImg:backgroundImg
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
    background: url('./assets/18.jpg');
    background-size: 100%;
      #app{
        height: 100%;
        width: 100%;
        // position: relative;
        .background{
          position: relative;
          font-size: 0;
        }
        .main{
          width: 100vw;
          height: 100vh;
          // margin-left: 10vh;
          .content{
            // border: 1px solid black;
            margin: 0 auto;
            background-color: rgba(255,255,255,.5);
            width: 60vw;
            height: 100vh;
          }
        }
        .Sidebar{
          position: fixed;
          top: 20vh;
          background-color: rgba(0, 0, 0, 0.8);
          border-right: 1px solid rgba(0, 0, 0, 0.5);
          box-shadow: 1vh 1vh 2vh 0vh rgba(0, 0, 0, 0.6);
          width: 10vh;
          // height: 100vh;
        }
    }
  }
}
</style>
