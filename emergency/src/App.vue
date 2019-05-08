<template>
  <div id="app">
    <ChengJi/>
    
      <div>
        <DanXuanKuang/>
        <DaoJiShi></DaoJiShi>
      </div>
      <div>
         <DaoJiShi2 @time-end="message = '倒计时结束'" :endTime='endTime'></DaoJiShi2>
         <p>{{message}}</p> 
      </div>

  </div>
</template>

<script>


import DaoJiShi2 from './components/DaoJiShi2'
import DanXuanKuang from './components/DanXuanKuang'

export default {
  name: 'App',
  components: {


    DanXuanKuang,

    DaoJiShi2
  },
  data(){
    return{
      message:'正在倒计时',
      endTime : '2019-07-08 10:06:00'
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
