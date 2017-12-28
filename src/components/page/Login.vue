<template>
    <div class="login-wrap" id="menu">
        <canvas id="canvas" class="canvas"></canvas>
        <div class="ms-title">个人前端系统</div>
        <div class="ms-login">
            <el-form :model="ruleForm" :rules="rules" ref="ruleForm" label-width="0px" class="demo-ruleForm">
                <el-form-item prop="username">
                    <el-input v-model="ruleForm.username" placeholder="username"></el-input>
                </el-form-item>
                <el-form-item prop="password">
                    <el-input type="password" placeholder="password" v-model="ruleForm.password" @keyup.enter.native="submitForm('ruleForm')"></el-input>
                </el-form-item>
                <div class="login-btn">
                    <el-button type="primary" @click="submitForm('ruleForm')">登录</el-button>
                </div>
                <p style="font-size:12px;line-height:30px;color:#999;">提示: 用户名和密码随便填！</p>
            </el-form>
        </div>
    </div>
</template>

<script>

import Stars from '../../../static/js/Star'
import Moon from '../../../static/js/Moon'
import Meteor   from '../../../static/js/Meteor'
    export default {
        data: function(){
            return {
                ruleForm: {
                    username: '',
                    password: ''
                },
                rules: {
                    username: [
                        { required: true, message: '请输入用户名', trigger: 'blur' }
                    ],
                    password: [
                        { required: true, message: '请输入密码', trigger: 'blur' }
                    ]
                }
            }
        },
        methods: {
            submitForm(formName) {
                const self = this;
                self.$refs[formName].validate((valid) => {
                    if (valid) {
                        localStorage.setItem('ms_username',self.ruleForm.username);
                        self.$router.push('/readme');
                    } else {
                        console.log('error submit!!');
                        return false;
                    }
                });
            }
        },
	    mounted(){
		let canvas = document.getElementById('canvas'),
		    ctx = canvas.getContext('2d'),
		    width = window.innerWidth,
		    height = window.innerHeight,
		    //实例化月亮和星星。流星是随机时间生成，所以只初始化数组
		    moon = new Moon(ctx, width, height),
		    stars = new Stars(ctx, width, height, 200),
		    meteors = [],
		    count = 0

		    canvas.width = width;
		    canvas.height = height;

		const meteorGenerator = ()=> {
		    //x位置偏移，以免经过月亮
		    let x = Math.random() * width + 800
		    meteors.push(new Meteor(ctx, x, height))

		    //每隔随机时间，生成新流星
		    setTimeout(()=> {
		        meteorGenerator()

		    }, Math.random() * 2000)
		}

		const frame = ()=>{
		    count++
		    count % 10 == 0 && stars.blink()
		    moon.draw()
		    stars.draw()

		    meteors.forEach((meteor, index, arr)=> {
		        //如果流星离开视野之内，销毁流星实例，回收内存
		        if (meteor.flow()) {
		            meteor.draw()
		        } else {
		            arr.splice(index, 1)
		        }
		    })
		    requestAnimationFrame(frame)
		}
		meteorGenerator()
		frame()
	}
    }
</script>

<style scoped>
#menu {
	height: 100%;
	overflow: hidden;
	position: relative;
}

    .login-wrap{
        width:100%;
    }
    .ms-title{
        position: absolute;
        top:50%;
        width:100%;
        margin-top: -230px;
        text-align: center;
        font-size:30px;
        color: #fff;

    }
    .ms-login{
        position: absolute;
        left:50%;
        top:50%;
        width:300px;
        height:160px;
        margin:-150px 0 0 -190px;
        padding:40px;
        border-radius: 5px;
        background: #fff;
        opacity: 0.88;
    }
    .login-btn{
        text-align: center;
    }
    .login-btn button{
        width:100%;
        height:36px;
    }
</style>