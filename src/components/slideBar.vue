<template>
  <div class="container bar-main">
    <ul class="column main-ul">
      <li class="userImg">
        <img src="../assets/userimg.jpg" class="">
        <p>{{userName}}</p>
      </li>
      <li class="log">
        <span>{{logNum}}</span>
        <P>日志</P>
      </li>
      <li class="log">
        <span>{{projectNum}}</span>
        <P>项目</P>
      </li>
      <li>
        <a href="" class="github">
          <img src="../assets/github.svg" class="github-img">
          <span></span>
          <p>Github</p>
        </a>
      </li>
      <li></li>
    </ul>
  </div>
</template>

<script>
export default{
  data(){
    return{
      userName:'Chris',
      logNum:'10',
      projectNum:'1'
    }
  }
}
</script>

<style lang="scss" scoped>
  .bar-main{
    .main-ul{
      width: 100%;
      height: 100%;
      li{
        cursor: pointer;
        margin-top: 5vh;
        position: relative;
        .github{
          height: 10vh;
          span{
            height: 3.3vh;
            width: 3.3vh;
            position: absolute;
            top: 0.4vh;
            left: 1.6vh;
            background-color: #fff;
            border-radius: 45%;
            z-index: -1;
          }
          .github-img{
            width: 4vh;
            height: 4vh;
            }
          p{
            color: #fff;
            font-size: 14px;
            padding-top: 1vh;
          }
        }
      }
      .userImg{
        img{
          width: 5vh;
          height: 5vh;
          border-radius: 50%;
        }
        p{
          color: #fff;
          font-size: 17px;
          padding-top: 1vh;
        }
      }
      .log{
        color: rgb(189, 189, 189);
        font-size: 15px;
        &:hover{
          color: #fff;
        }
        span{
          font-size: 19px;
        }
        p{
          padding-top: 1vh;
        }
      }
    }
  }
</style>
