<template>
  <div id='Test' class='test'>
    <h1 style="text-align: center;">应急演练</h1>
    <el-form ref="form" :model="form" label-width="80px" :rules="rules">
      <!-- <el-form-item label="test" prop="test">
        <el-input v-model="form.test"></el-input>
      </el-form-item> -->
      <el-form-item label="应急预案" prop="selectedOptions">
        <el-cascader
        :options="form.options"
        placeholder="请选择应急预案"
        v-model="form.selectedOptions"
        @change="handleChange">
        </el-cascader>
      </el-form-item>
      <el-form-item label="触发时间" prop="date1">
        <el-date-picker
          v-model="form.date1"
          type="datetime"
          placeholder="选择日期时间"
          align="right"
          :picker-options="pickerOptions">
        </el-date-picker>
      </el-form-item>
      <el-form-item>
        <el-button type="primary" @click="onSubmit('form')">立即创建</el-button>
        <el-button  @click="resetForm('form')">取消</el-button>
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
/* eslint-disable */
  export default {
    name: 'Test',
    data() {
      return {
        DrillNum:'',
        rules:{
          // test:[{ required: true, message: '请输入活动名称', trigger: 'blur' }],
          selectedOptions:[ { required: true, message: '请选应急预案', trigger: 'change' }],
          date1:[{ type:'date',required: true,message:'请选择日期',trigger:'change'}]
        },
        form: {
          // test:'',
          date1: '',
          selectedOptions: [],
          options: [{value: 'WL001',label: 'WL001-广域网单边链路中断应急预案',
                    children: [{value: '001',label: '主节点',},
                              {value: '002',label: '备节点',}]
                    }, 
                    {value: 'WL002',label: 'WL002-广域网单边链路丢包应急预案',
                    children: [{value: '003',label: '主节点',}, 
                                {value: '004',label: '备节点',}]},
                    {value:'005',label:'WL003-次生产互联网区域YZXCRT03路由器故障应急预案'},
                    {value: '006',label: 'WL004-次生产区域第三方IpSec接入网关第一台YZXIPSECFW04故障应急预案'},
                    {value: '007',label: 'WL005-次生产区域第三方IpSec接入网关第二台YZXIPSECFW05故障应急预案'},
                    {value: '008',label: 'WL006-次生产区域第三方路由器故障应急预案'},
                    {value: '009',label: 'WL007-省市体彩中心数据端二次认证服务失效应急预案 '},
                    {value: '010',label: 'XT001-虚拟化环境rtp单机失效启用备机应急预案'},
                    {value: '011',label: 'XT002-高频Windows群集故障应急预案'},
                    {value: '012',label: 'XT004-高频数据库主节点NTP服务异常停止应急预案'},
                    {value: '013',label: 'XT005-乐透二代GoldenGate包状态异常应急预案'},
                    {value: '014',label: 'XT006-ESXi宿主机网络隔离故障应急预案'},
                    {value: '015',label: 'AQ001-SSL网关异常宕机应急预案'},
                    {value: '016',label: 'AQ002-从LDAP服务器进程异常停止应急预案'},
                  ],
        },
        pickerOptions: {
          shortcuts: [{
            text: '三十秒过后',
            onClick(picker) {
              const date = new Date();
              date.setTime(date.getTime() + 30 * 1000 );
              picker.$emit('pick', date);
            }
          },{
            text: '五分钟后',
            onClick(picker) {
              const date = new Date();
              date.setTime(date.getTime() + 60 * 1000 * 5);
              picker.$emit('pick', date);
            }
          },{
            text: '十分钟后',
            onClick(picker) {
              const date = new Date();
              date.setTime(date.getTime() + 60 * 1000 * 10);
              picker.$emit('pick', date);
            }
          },{
            text: '二十分钟后',
            onClick(picker) {
              const date = new Date();
              date.setTime(date.getTime() + 60 * 1000 * 20);
              picker.$emit('pick', date);
            }
          },{
            text: '三十分钟后',
            onClick(picker) {
              const date = new Date();
              date.setTime(date.getTime() + 60 * 1000 * 30);
              picker.$emit('pick', date);
            }
          },{
            text: '今天',
            onClick(picker) {
              picker.$emit('pick', new Date());
            }
          }, {
            text: '明天',
            onClick(picker) {
              const date = new Date();
              date.setTime(date.getTime() + 3600 * 1000 * 24);
              picker.$emit('pick', date);
            }
          }, {
            text: '后天',
            onClick(picker) {
              const date = new Date();
              date.setTime(date.getTime() + 3600 * 1000 * 24 * 2);
              picker.$emit('pick', date);
            }
          }]
        },
      };
    },

    // 上面全是数据
    methods: {
      handleChange(value) {
        if(value[1]){
          this.DrillNum = value[1];
        }
        else{
          this.DrillNum = value[0];
        }
      },
      onSubmit(form){
        this.$refs[form].validate((valid) => {
          if (valid) {
            // alert('submit!');
            this.$emit("getForminformation",this.form.date1,this.DrillNum);
          } else {
            alert('error submit!! 请联系管理员');
            return false;
          }
        });
        // tep = this.form.date1+this.form.date2;
        // this.$emit("formSubmit",this.form.date1)
        // alert(this.form.date1)
        // console.log(this.form.options)
      },
      resetForm(form){
        this.$refs[form].resetFields();
      }
    }
  };
</script>


<style>
.test{
    border: 1px solid #DCDFE6;
    width: 400px;
    margin: 10px auto;
    padding: 35px 35px 15px 35px;
    border-radius: 5px;
    -webkit-border-radius: 5px;
    margin-bottom: 10px auto;
    -moz-border-radius: 5px;
    box-shadow: 0 0 20px #909399;
}
.transition-box {
  margin-bottom: 10px auto;
  width: 350px;
  height: 150px;
  border-radius: 4px;
  /*background-color: #409EFF;*/
  text-align: center;
  color: red;
  padding: 10px 20px;
  box-sizing: border-box;
  margin: 20px auto;
  font-weight: bold;
  font-size:25px;
  /*font-family:Georgia;*/
}
/*#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
div {
  width: 300px;
  height: 300px;
  margin: 30px auto;
  border: 1px solid red;

}*/
</style>
