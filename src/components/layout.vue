<template>
	<el-container class="container">
		<el-header>
			<div class="logout" @click="logout">
				<i class="icon iconfont icon-poweroff"></i>
			</div>
			<div class="header-bar">
				<router-link to="/home" >
					<div class="logo"><img src="../image/logo.png" alt="" srcset=""></div>
					<div class="proj-name">中小企业征信平台</div>
				</router-link>
			</div>
		</el-header>
		<el-main>
			<router-view/>
		</el-main>
		<!--<el-footer>Footer</el-footer>-->
	</el-container>
</template>

<script>
export default {
  methods: {
    logout() {
      this.$confirm("退出系统, 是否继续?", "提示", {
        confirmButtonText: "确定",
        cancelButtonText: "取消",
        type: "warning",
        center: true
      }).then(() => {
		sessionStorage.removeItem("token");
        this.$router.push({path:'/login'})
      },()=>{

	  });
    }
  }
};
</script>

<style lang="scss" scoped>
@import "@/style/commonStyle.scss";
.container {
  height: 100%;
  min-width: 1300px;
  .el-header {
    padding: 0;
    background-color: #2d2d2d;
    color: #fff;
    .header-bar {
      height: inherit;
      font-size: 0;
      .logo {
        display: inline-block;
        margin: 11px 15px 0 30px;
        vertical-align: top;
      }
      .proj-name {
        margin-top: 14px;
        padding-left: 15px;
        display: inline-block;
        line-height: 33px;
        border-left: 2px solid #fff;
        font-size: 18px;
		color:#fff;
      }
    }
    .logout {
      float: right;
      display: flex;
      justify-content: center;
      align-items: center;
      margin-right: 22px;
      height: inherit;
      .icon {
        cursor: pointer;
        &:hover {
          color: #1790ff;
        }
      }
    }
  }

  .el-main {
    padding: 0;
    background-color: $background-color-main;
  }
}
</style>

