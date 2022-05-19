
<template>
  <el-container>
    <el-header>小清单
        <!-- <todoheader /> -->
        <button @click="logoutHandler" class="logout-btn">退出</button>
    </el-header>
    <el-main>
      <el-row type="flex" justify="center">
        <el-col :xs="20" :span="12" >
          <div class="grid-content">
            <router-view/>
          </div>
        </el-col>
      </el-row>
    </el-main>
    <el-footer> 友情链接： </el-footer>
  </el-container>
</template>
<script>
// import todoheader from "@/components/header.vue";

export default {
  name: 'App',
  // components:{
  //   todoheader
  // }
   methods:{
	  logoutHandler(){
		  // let username = window.localStorage.getItem('name','')
		  // let access_token = window.localStorage.getItem('access_token','')
		  // let params = {
			//   access_token:access_token
		  // }
		  this.$http.logout()
		  .then(res=>{
			  console.log(res)
			  if(res.code === 200){
				  this.$router.push({
					  name:"Login"
				  });
				  localStorage.removeItem('access_token')
				  localStorage.removeItem('name')
			  }
		  }).catch(err=>{
			  console.log(err);
		  })

	  }
  }
}
</script>

<style scoped>
.logout-btn{
  margin-top:15px;
  float: right;
}
.el-header,
.el-footer {
  background-color: #409eff;
  color: #fff;
  text-align: center;
  line-height: 60px;
}
.el-footer {
  background-color: #909399;
  display: block;
  width: 100%;
  position: fixed;
  bottom: 0;
}

</style>
