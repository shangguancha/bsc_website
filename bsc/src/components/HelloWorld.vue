<template>
  <div class="hello">
   <el-container>
  <el-header>{{msg}}</el-header>
  <el-main>
    
  <el-row>
   <el-col :span="4"><div class="grid-content bg-purple-dark">
     <el-input v-model="address" placeholder="请输入合约地址"></el-input>
     </div>
   </el-col>
 
  </el-row>
     <el-row>
   <el-col :span="4"><div class="grid-content bg-purple-dark">
         <el-input type="textarea" v-model="callbackInfo"></el-input>
  </div></el-col>
 
  </el-row>
  <el-row>
    <el-button type="primary" @click="onSubmit">确定</el-button>
  </el-row>



  </el-main>
     <el-footer>Footer</el-footer>
</el-container>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: '根据你的目的查询你的信息！',
      address:'',
      callbackInfo:''
  }
},methods:{
    onSubmit:function (){ 
      let ss = this;
       this.$axios.get(" https://api.bscscan.com/api",{
         'apikey':'53HGI7RG1BB3RSWM6PAXM2BU9C3NYVJ264',
         'module':'account',
         'action':'balance',
         'address':ss.address
       }).then(function(response){
          ss.callbackInfo = JSON.stringify(response.data);
       })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .el-header, .el-footer {
    background-color: rgb(123, 156, 199);
    color: #333;
    text-align: center;
    line-height: 60px;
 
  }
  
  
  .el-main {
    background-color: #E9EEF3;
    color: #333;
    text-align: center;
    height: 800px;
  }
  
   .el-row {
    margin-bottom: 20px;
  }
  .el-col {
    border-radius: 4px;
  }
  .bg-purple-dark {
    background: #99a9bf;
  }
  .bg-purple {
    background: #d3dce6;
  }
  .bg-purple-light {
    background: #e5e9f2;
  }
  .grid-content {
    border-radius: 4px;
    min-height: 36px;
  }
  .row-bg {
    padding: 10px 0;
    background-color: #f9fafc;
  
  }
 
</style>