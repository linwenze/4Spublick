<template>
	<div id="subNavview">
		<el-row class="crownpin-top">
	        <el-col :span="18">
	          <div style="width: 50px;height: 50px;background: #1494eb;display: inline-block;vertical-align: middle;margin: -2px 5px 0 0;"></div>
	          <i class="scrm-icon scrm-icon-16 scrm-classify"></i>
	          <!--子导航路由循环-->
	          <a @click="goUp(item.path)" class="changecolor" v-for="item in subbread">
	          	<span class="top-module m-l-5">{{item.name}}</span>
	          	<i class="el-icon-arrow-right"></i>
	          </a>
	           <!-- 子导航最后一个为不可点击的-->
	           <span class="top-module m-l-5">{{arrlist[arrlist.length-1].name}}</span>
	        </el-col>
	        <el-col :span="6" class="text-right">
	          <router-link to="/index" class="icon">
	            <i class="scrm-icon scrm-icon-16 scrm-myorder"></i>
	            <span class="m-l-5 text-blue">使用教程</span>
	          </router-link>
	        </el-col>
	     </el-row>
     </div>
</template>
<script>
	export default{
		created(){   //页面创建完成立即获取面包屑相关资料
			this.getbreadcrumb();
			this.subbreadcrumb()
		},
		data(){
			return {
                    brumblist:[],
                    arrlist:[],
                    subbread:[]
			}
		},
		methods:{
			
			goUp(routerUrl){  //面包屑导航跳转相应的路由
              this.$router.push(routerUrl)
			},
			
			subbreadcrumb(){  //设置中间值存储面包屑相关信息
                this.subbread = this.arrlist.splice(0,this.arrlist.length-1)
               
			},
			getbreadcrumb(){  //获取面包屑路由
			  let That = this;
		      this.brumblist = this.$route.matched;
		      this.brumblist.forEach(item =>{
                    if(item.name !=undefined){
                    	That.arrlist.push({name:item.name,path:item.path})
                    }
		      })
		    },
		}
	}
</script>
<style lang="scss" scoped>
.crownpin-top {
  font-size: 14px;
  background: #ffffff;
  border-radius: 5px;
  box-shadow: 0 0 10px 2px rgba(0, 0, 0, .05);
  margin: 0 30px 20px;
  height: 50px;
  line-height: 50px;
  padding-right: 15px;
}
.changecolor{
	color:#1395eb;
}
</style>