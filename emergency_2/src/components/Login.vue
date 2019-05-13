<template>
  <div id="Login">
    <h1>登陆界面</h1>
    <form v-on:submit="UserLogin">
      <input type="text" name="useename" v-model="username" placeholder="用户名">
      <input type="password" name="password" v-model="password" placeholder="密码">
      <input type="submit" name="登录">
    </form>
  </div>
</template>

<script>
/* eslint-disable */
export default {
  name: 'Login',
  data: function(){
    return{
      username: "",
      password: ""
    }
  },
  methods: {
    UserLogin: function(e){
      // alert("good job")
      if(this.username=='admin'&&this.password=='passwd'){
        console.log(111);
        this.$router.push('/index')
      }
      else{
        console.log(222222)
      }
      e.preventDefault();
      
        // this.$axios({
        //   methods: 'post',
        //   url:'http://127.0.0.1:5000/login',
        //   data:{
        //     username:this.username,
        //     password:this.password,
        //   }
        // }).then((response) => {
        //   console.log(response)
        // }).catch((error)=>{
        //   console.log(error)
        // })
      
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
