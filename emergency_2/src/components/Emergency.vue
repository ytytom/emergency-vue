<template>
  <div id="Emergency">
    <Test v-on:getForminformation="Getformitem"></Test>
    <div class="transition-box">
    <DaoJiShi @time-end="EmergencyAction" :endTime='endTime'></DaoJiShi>
    <P v-if="endTime">{{message}}</P>
    </div>
  </div>
</template>

<script>
/* eslint-disable */
// import DateTimePicker from '@/components/DateTimePicker'
import Test from '@/components/Test'
import DaoJiShi from '@/components/DaoJiShi'
export default {
  name: 'Emergency',
  components: {
    // DateTimePicker,
    Test,
    DaoJiShi
  },
  data(){
    return{
      DrillNum: '',
      message: '正在倒计时',
      endTime: ''
    }
  },
  methods: {
    // EmergencyAction: function(){
    //   alert("hello world!")
    // },
    Getformitem:function(text,DrillNum){
      // alert(DrillNum)
      this.DrillNum = DrillNum
      // 已经拿到drillnum了
      // alert(text)
      // this.endTime = String(text)
      // alert(this.endTime)
      this.$axios({
        methods:'post',
        url:'http://127.0.0.1:5001/time',
        data:{
          data1:text
        }
      }).then((response) => {
          console.log(response)
        }).catch((error)=>{
          console.log(error)
        })
    },
    EmergencyAction:function(){
      this.message='倒计时结束 正在处理！';
      alert(this.DrillNum)
      this.$axios({
          methods: 'get',
          url:'http://127.0.0.1:5000/emergency/'+this.DrillNum,
        }).then((response) => {
          console.log(response)
        }).catch((error)=>{
          console.log(error)
        })
      this.message='处理成功，大概需要5S左右触发告警'
    }
  }
}


</script>

<style>

</style>
