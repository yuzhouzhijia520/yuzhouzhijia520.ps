<template>
    <div class="header clearFloat">
        <div class="logo"><span class="logoTitle1">Watch For </span><span class="logoTitle2">The Happies</span></div>
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
<style>
article, aside, figure, figcaption, footer, header, hgroup, nav, section, summary {  
  display: block;  
}

body {
  font: 300 13px/20px 'Open Sans', Arial, sans-serif;
  overflow-x: hidden;
}

header {
  background-color: #2D9900;
  border: thin #336699 solid;
  padding: 10px;
  margin: 10px;
  text-align: center;
}

header h1 {
  margin: 0px;
  color: white;
  font-size: xx-large;
}

header h2 {
  margin: 0px;
  font-weight: bold;
}

header .Teaser {
  font-size: large;
  font-weight: bold;
}

header .Byline {
  font-style: italic;
  font-size: small;
  margin: 0px;
}

.Content {
    padding-bottom: 5px;
    line-height: 120%;
    text-align: center;
}

.Content .LeadIn {
  font-weight: bold;
  font-size: large;
  font-variant: small-caps;
}

.Content h2 {
  color: #24486C;
  margin-bottom: 2px;
  font-size: medium;
}

.Content p {
  margin-top: 0px;
}

footer {
  text-align: center;
  font-size: x-small;  
}

footer .Disclaimer {
  font-style: italic;
}

footer p {
  margin: 3px;
}
	</style>
<style lang="less">
    @font-face{
        font-family: 'FoglihtenFr02';
        src : url('../../../static/fonts/FoglihtenFr02.otf');
    }
    .clear{
        clear: both;
    }
    .clearFloat:after{
        display: block;
        content: '.';
        clear: both;
        visibility: hidden;
        height: 0;
    }
    .clearFloat{
        zoom: 1;
    }
    .header {
        position: relative;
        box-sizing: border-box;
        width: 100%;
        height: 96px;
        line-height: 70px;
        font-size: 67px;
        margin-top: 32px;
    }
    .header .logo{
        text-align: center;
        font-family: 'FoglihtenFr02';
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
        margin-right: -38%;
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
