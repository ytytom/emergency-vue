<template>
  <div id="Emergency">
    <form v-on:submit="EmergencyAction">
      <el-select v-modle="Drill_num" placeholder="请选择预案编号">
        <el-option value="shanghai">次生产区域第三方IpSec接入网关第一台YZXIPSECFW04故障应急预案</el-option>
        <el-option value="beijing">省市体彩中心数据端二次认证服务失效应急预案</el-option>
      </el-select>
      <br>
      <br>
      <br>
      <DateTimePicker type="datetime-local" name="time" v-model='date'></DateTimePicker>
      <br>
      <el-button type="primary" @click="onSubmit">立即创建</el-button>
      <el-button>取消</el-button>
    </form>
  </div>
</template>

<script>
/* eslint-disable */
import DateTimePicker from '@/components/DateTimePicker'
export default {
  name: 'Emergency',
  data(){
    return{
      date,
      Drill_num
    }
  },
  components: {
    DateTimePicker
  },
  methods: {
    onSubmit() {
      alert('submit!');
    }
  }
}
</script>

<style>

</style>
