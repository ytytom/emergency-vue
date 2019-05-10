<template>
  <div id='Test' class='test'>
    <el-form ref="form" :model="form" label-width="80px" :rules="rules">
      <el-form-item label="test" prop="test">
        <el-input v-model="form.test"></el-input>
      </el-form-item>
      <el-form-item label="应急预案" prop="drill">
        <el-cascader
        :options="form.options"
        placeholder="请选择应急预案"
        v-model="selectedOptions"
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
      <el-button type="primary" @click="onSubmit('form')">立即创建</el-button>
      <el-button type="reset" @click="resetForm('form')">取消</el-button>
    </el-form>
  </div>
</template>

<script>
/* eslint-disable */
  export default {
    name: 'Test',
    data() {
      return {
        rules:{
          test:[{ required: true, message: '请输入活动名称', trigger: 'blur' }],
          date1:[{ type:'date',required: true,message:'请选择日期',trigger:'change'}]
        },
        form: {
          test:'',
          date1: '',
          options: [{value: 'WL001',label: '广域网单边链路中断应急预案',
                    children: [{value: '001',label: '主节点',},
                              {value: '002',label: '备节点',}]
                    }, 
                    {value: 'WL002',label: '广域网单边链路丢包应急预案',
                    children: [{value: '003',label: '主节点',}, 
                                {value: '004',label: '备节点',}]},
                    {value:'WL003',label:'次生产互联网区域YZXCRT03路由器故障应急预案'},
                    {value: 'ziyuan',label: '资源',
                    children: [{value: 'axure',label: 'Axure Components'},
                               {value: 'sketch',label: 'Sketch Templates'},
                                {value: 'jiaohu',label: '组件交互文档' }]
                    }],
        },
        pickerOptions: {
          shortcuts: [{
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
        selectedOptions: [],
        
      };
    },

    // 上面全是数据
    methods: {
      handleChange(value) {
        if(value[1]){
          console.log(value[1]);
        }
        else{
          console.log(value[0]);
        }
      },
      onSubmit(form){
        this.$refs[form].validate((valid) => {
          if (valid) {
            alert('submit!');
          } else {
            console.log('error submit!!');
            return false;
          }
        });
        // tep = this.form.date1+this.form.date2;
        this.$emit("formSubmit",this.form.date1)
        // alert(this.form.date1)
        // console.log(this.form.options)
      },
      ResetOptions(formName){
        this.$refs[formName].resetFields();
      }
    }
  };
</script>


<style>
.test{
  border: 1px solid #DCDFE6;
    width: 350px;
    margin: 180px auto;
    padding: 35px 35px 15px 35px;
    border-radius: 5px;
    -webkit-border-radius: 5px;
    -moz-border-radius: 5px;
    box-shadow: 0 0 250px #909399;
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
