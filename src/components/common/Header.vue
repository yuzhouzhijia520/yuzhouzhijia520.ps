<template>
    <div class="header">
        <div class="logo"><span class="logoTitle1">守望</span><span class="logoTitle2">幸福</span></div>
        <div class="user-info">
            <el-dropdown trigger="click" @command="handleCommand">
                <span class="el-dropdown-link">
                    <img class="user-logo" src="../../../static/img/img.jpg">
                    {{username}}
                </span>
                <el-dropdown-menu slot="dropdown">
                    <el-dropdown-item command="loginout">退出</el-dropdown-item>
                </el-dropdown-menu>
            </el-dropdown>
        </div>
    </div>
</template>
<script>
    export default {
        data() {
            return {
                name: 'songsongs'
            }
        },
        computed:{
            username(){
                let username = localStorage.getItem('ms_username');
                return username ? username : this.name;
            }
        },
        methods:{
            handleCommand(command) {
                if(command == 'loginout'){
                    localStorage.removeItem('ms_username')
                    this.$router.push('/login');
                }
            }
        }
    }
</script>
<style lang="less">
    .header {
        position: relative;
        box-sizing: border-box;
        width: 100%;
        height: 70px;
        line-height: 70px;
        font-size: 67px;
        margin-top: 32px;
    }
    .header .logo{
        text-align: center;
        .logoTitle1{
            color: #B1B63D;
        }
        .logoTitle2{
            color: #B95429;
        }
    }
    .user-info {
        float: right;
        padding-right: 50px;
        font-size: 16px;
        margin-top: -90px;//.header {height:70px;margin-top:20px}=90px
    }
    .user-info .el-dropdown-link{
        position: relative;
        display: inline-block;
        padding-left: 50px;
        cursor: pointer;
        vertical-align: middle;
    }
    .user-info .user-logo{
        position: absolute;
        left:0;
        top:15px;
        width:40px;
        height:40px;
        border-radius: 50%;
    }
    .el-dropdown-menu__item{
        text-align: center;
    }
    .el-dropdown-menu{
            background-color: transparent;
            border-image: linear-gradient( #00ff1f , #a903bb) 10 20;
            .el-dropdown-menu__item:not(.is-disabled):hover{
                    background-color: transparent;
            }
    }
</style>
