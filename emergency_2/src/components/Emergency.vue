<template>
  <div id="Emergency">
    <div>应急预案编号</div>
    <Test v-on:formSubmit="Getformitem"></Test>
    <DaoJiShi @time-end="message='倒计时结束'" :endTime='endTime'></DaoJiShi>
    <P v-if="endTime">{{message}}</P>
  </div>
</template>

<script>
/* eslint-disable */
import DateTimePicker from '@/components/DateTimePicker'
import Test from '@/components/Test'
import DaoJiShi from '@/components/DaoJiShi'
export default {
  name: 'Emergency',
  components: {
    DateTimePicker,
    Test,
    DaoJiShi
  },
  data(){
    return{
      message: '正在倒计时',
      endTime: ''
    }
  },
  methods: {
    EmergencyAction: function(){
      alert("hello world!")
    },
    Getformitem:function(text){
      console.log(111111111111111111111111)
      // alert(text)
      this.endTime = text
    }
  }

}
</script>

<style>


</style>
