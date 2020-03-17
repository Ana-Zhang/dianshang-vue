<template>
	<div class="login_container">
    	<div class="login_box">
    	<!-- 头像区域 -->
    		<div class="avatar_box">
    	    	<img src="../assets/logo.png" alt="">
    		</div>
    	<!-- 登录表单区域 -->
			<!-- ref引用一个名词 -->
    		<el-form ref="loginFormRef" :model="loginForm" :rules="loginFormRules" label-width="0px" class="login_from">
			<!-- 用户名区域 -->
				<el-form-item label="" prop="uesrname">
					<el-input v-model="loginForm.uesrname" placeholder="请输入账号" prefix-icon="el-icon-user-solid">
					</el-input>
				</el-form-item>

			<!-- 密码区域 -->
				<el-form-item label="" prop="password">
					<el-input v-model="loginForm.password" placeholder="请输入密码" prefix-icon="el-icon-lock" type="password">
					</el-input>
				</el-form-item>

			<!-- 按钮区域 -->
				<el-form-item label="" class="btns">
					<el-button type="primary" @click="login">登录</el-button>
					<el-button type="info" @click="resetLoginForm">重置</el-button>
				</el-form-item>
    		</el-form>
    	</div>
	</div>
</template>

<script>

export default {
	data() {
		return {
			// 这是登录表单的数据绑定对象，是个对象所以{}
			loginForm: {
				uesrname: "zs",
				password: "123"
			},
			// 这是登录规则绑定对象
			loginFormRules: {
				// 验证用户名是否合法
				uesrname: [
					 { required: true, message: '请输入用户名称', trigger: 'blur' },
					 { min: 3, max: 5, message: '长度在 3 到 5 个字符', trigger: 'blur' }
				],
				// 验证密码是否合法
				password: [
					{ required: true, message: '请输入用户密码', trigger: 'blur' },
					{ min: 6, max: 15, message: '长度在 6 到 15 个字符', trigger: 'blur' }
				]
			}
		};
	},
	methods: {
		// 点击重置按钮，重置表单
		resetLoginForm() {
			// console.log(this)
			this.$refs.loginFormRef.resetFields();
		},
		login() {
			this.$refs.loginFormRef.validate(Boolean => {
				console.log(Boolean)
			})
			// console.log(this);
		}
	}
};

</script>

<style lang="less" scoped>
.login_container{
	background-color: #2b4b6b;
    height: 100%;
}

.login_box{
    width: 450px;
    height: 300px;
    border-radius: 3px;
    background-color: #fff;
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%,-50%);
}

.avatar_box{
    width: 130px;
    height: 130px;
    padding: 10px;
    border-radius: 50%;
    border: 1px solid #eee;
    background-color: #fff;
    box-shadow: 0 0 10px #ddd;
    position: absolute;
    left: 50%;
    transform: translate(-50%,-50%);
    img{
    	width: 100%;
    	height: 100%;
    	border-radius: 50%;
    	background-color: #eee;
    }
}

.login_from{
	width: 100%;
	padding: 0 10px;
	box-sizing: border-box;
	position: absolute;
	bottom: 0px;
}
	
.btns{
	float: right;
}

</style>
