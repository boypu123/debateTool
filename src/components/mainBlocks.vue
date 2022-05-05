<script>
// 从NaiveUI中引入NButton组件
import { NButton } from 'naive-ui'
export default ({
  // Register Components
  components: {
    NButton
  },
  // data
  data() {
    return {
      howManyTimes: 0,
      stopWatch:{
        // 初始化时间
        seconds: 0,
        minutes: 0,
        status: false
      },
    }
  },
  // methods
  methods: {
    //秒表
    startStopWatch(){
      // 判断是否已经开始
        // 开始计时
          if (this.stopWatch.status == true){
            alert("已经开始了，不能再开始了！")
            return;
          }
        this.stopWatch.timer = setInterval(() => {
          this.stopWatch.status = true;
          this.stopWatch.seconds++;
          if(this.stopWatch.seconds === 60){
            this.stopWatch.seconds = 0;
            this.stopWatch.minutes++;
          }
        }, 1000);
    },
    pauseStopWatch(){
      // 判断是否已经开始
      // 暂停计时
      clearInterval(this.stopWatch.timer);
      this.stopWatch.status = false;
    },
    resetStopWatch(){
      this.stopWatch.seconds = 0;
      this.stopWatch.minutes = 0;
      clearInterval(this.stopWatch.timer);
      this.stopWatch.status = false;
    },
  },
  //props
  props: {
    msg: String
  }

})
</script>

<template>
  <div id="main">
    <div style="margin-left:30px; font-size: 44px; font-weight: bold;">{{ msg || 'No Props Passed Yet'}}</div>
    <n-button type="primary" style="margin: 86px 30px; width:82px;" @click="this.howManyTimes++"> +1 次数</n-button>
    <n-button type="error" style="position:absolute; margin: 141px -112px; width:82px;" @click="this.howManyTimes--">-1 次数</n-button>
    <div id="timerText">{{stopWatch.minutes}}:{{stopWatch.seconds}}</div>
    <div style="margin-left: 270px; position:absolute; font-size: 20px; font-weight: bold;">正计时</div>
    <n-button type="info" id="timerButton" style="margin-left: 40px; margin-top: 300px;" @click="startStopWatch()">开始</n-button>
    <n-button type="error" id="timerButton" style="margin-left: 120px; margin-top: 300px;" @click="pauseStopWatch()">暂停</n-button>
    <n-button type="warning" id="timerButton" style="margin-left: 200px; margin-top: 300px;" @click="resetStopWatch()">重置</n-button>
    <div style="font-size: 27px; margin-left:200px; margin-top: 200px; position:absolute; font-weight: bold;">已经辩论了{{howManyTimes}}次</div>
  </div>
</template>

<style>
  div{
    font-family: Source Han Sans CN;
      src: url(./fonts/SourceHanSansCN-Regular-2.otf);
  }
  #timerButton{
    width: 61px;
    height: 34px;
    position: absolute;
  }
  #timerText{
    position: absolute;
    margin-left: 200px;
    margin-top: -100px;
    width: 232px;
    height: 54px;
    font-size: 120px;
    font-weight: bold;
    line-height: 20px;
    letter-spacing: 0px;
    color: #000000;
    font-family: montserrat;
  }
  #main{
    border-radius: 20px;
    border: 5px solid #18A058;
    width: 550px;
    height: 550px;
    margin-left: 50px;
    margin-top: 20px;
  }
</style>
