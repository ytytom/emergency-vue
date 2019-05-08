<template>
    <div id="Emergency">
        <div>应急预案编号</div>
        <form v-on:submit="EmergencyAction">    
            <select>
                <option value="1">广域网单边链路中断应急预案</option>
                <option value="2">广域网单边链路丢包应急预案</option>
            </select>
            
            <input type="time"  value="13:55:59" >

            <input type="submit" value="提交">


        </form>       
    </div>
</template>

<script>
    export default {
        name:'EmergencyAction',
        data:function(){
            return{
                drill_num:""
            }
        },
        methods:{
        EmergencyAction:function(){

            alert("提交成功");
        }
        }
    }
</script>