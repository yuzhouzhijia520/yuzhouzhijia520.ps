<template>
    <div class="sidebar">
        <el-menu
 :default-active="onRoutes"
  class="el-menu-demo"
  mode="horizontal"
  background-color="#545c64"
  text-color="#fff"
  active-text-color="#ffd04b"
   unique-opened router>
            <!-- <template v-for="item in items"> -->
                <!-- <template v-if="item.subs">
                    <el-submenu :index="item.index" class="menuitemP">
                        <template slot="title"><i :class="item.icon"></i>{{ item.title }}</template>
                        <el-menu-item v-for="(subItem,i) in item.subs" :key="i" :index="subItem.index" class="menuitemC">{{ subItem.title }}
                        </el-menu-item>
                    </el-submenu>
                </template>
                <template v-else>
                    <el-menu-item :index="item.index">
                        <i :class="item.icon"></i>{{ item.title }}
                    </el-menu-item>
                </template> -->
                 <template v-for='item in items'>
                <!-- <el-menu
                :default-active="activeIndex2"
                class="el-menu-demo"
                mode="horizontal"
                background-color="#545c64"
                text-color="#fff"
                active-text-color="#ffd04b">
                <el-menu-item index="1">Home</el-menu-item> -->
                <!-- <el-submenu :index="item.index">
                    <template slot="title"><i :class="item.icon"></i>{{ item.title }}</template>
                    <el-menu-item v-for="(subItem,i) in item.subs" :key="i" :index="subItem.index" class="menuitemC">{{ subItem.title }}</el-menu-item>
                </el-submenu> -->
                <!-- <el-menu-item index="3"><a href="https://www.ele.me" target="_blank">Practice</a></el-menu-item>
                <el-menu-item index="4"><a href="https://www.ele.me" target="_blank">Work</a></el-menu-item>
                <el-menu-item index="5"><a href="https://www.ele.me" target="_blank">Gallery</a></el-menu-item>
                <el-menu-item index="6"><a href="https://www.ele.me" target="_blank">About</a></el-menu-item>
                <el-menu-item index="7"><a href="https://www.ele.me" target="_blank">Contact</a></el-menu-item> -->
                <template v-if="item.subs">
                    <el-submenu :index="item.index" class="menuitemP">
                        <template slot="title"><i :class="item.icon"></i>{{ item.title }}</template>
                        <el-menu-item v-for="(subItem,i) in item.subs" :key="i" :index="subItem.index" class="menuitemC">{{ subItem.title }}
                        </el-menu-item>
                    </el-submenu>
                </template>
                <template v-else>
                    <el-menu-item :index="item.index">
                        <i :class="item.icon"></i>{{ item.title }}
                    </el-menu-item>
                </template> 
                </template>
                </el-menu>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                activeIndex2: '1',
                items: [
                    {
                        icon: 'el-icon-setting',
                        index: 'readme',
                        title: 'Description'
                    },
                    {
                        icon: 'el-icon-menu',
                        index: '2',
                        title: 'Table',
                        subs: [
                            {
                                index: 'basetable',
                                title: 'Basic Table'
                            },
                            {
                                index: 'vuetable',
                                title: 'Vue Table'
                            }
                        ]
                    },
                    {
                        icon: 'el-icon-date',
                        index: '3',
                        title: 'Form',
                        subs: [
                            {
                                index: 'baseform',
                                title: 'TestForm'
                            },
                            {
                                index: 'vueeditor',
                                title: 'Editor'
                            },
                            {
                                index: 'markdown',
                                title: 'markdown'
                            },
                            {
                                index: 'upload',
                                title: 'upload'
                            }
                        ]
                    },
                    {
                        icon: 'el-icon-star-on',
                        index: 'basecharts',
                        title: 'D3.js'
                    },
                    {
                        icon: 'el-icon-upload2',
                        index: 'drag',
                        title: 'Drag'
                    },
                    {
                        icon: 'el-icon-upload2',
                        index: 'iForm',
                        title: 'iForm'
                    },
                    {
                        icon: 'el-icon-upload2',
                        index: 'myBlog',
                        title: 'myBlog'
                    },
                    {
                        icon: 'el-icon-upload2',
                        index: 'job',
                        title: 'job'
                    },
                    {
                        icon: 'el-icon-upload2',
                        index: 'EnJob',
                        title: 'EnJob'
                    }
                ]
            }
        },
        computed:{
            onRoutes(){
                return this.$route.path.replace('/','');
            }
        }
    }
</script>

<style lang="less"  >
    .sidebar{ 
        display: block;
        position: absolute;
        left: 25%;
        top: 130px;
        background: url(../../../static/img/tooplate_menu_bg.png) no-repeat;
        padding: 3px 39px;
        width: 994px;
        height: 60px;
    }
    .sidebar > ul {
        height: 80%;
        background: #B35127;
        .el-menu{

                   background-color: #AE4C24 !important;

            }
    }
    .el-menu--horizontal .el-menu-item{
        color: #fff;
    }
    .el-menu--horizontal .el-menu-item:hover{
        background: url(../../../static/img/tooplate_menu_item_r.png) right no-repeat;
    }
        
    ul.el-menu.el-menu-vertical-demo.el-menu--dark{
        background-color: transparent !important;
    }
    .el-menu--dark .el-menu-item:hover, .el-menu--dark .el-submenu__title:hover{
        background-color: transparent !important;
    }

    .menuitemP .el-menu--dark .el-menu-item:hover, .el-menu--dark .el-submenu__title:hover {
        background-color: transparent;
    }
    .el-menu--horizontal .el-submenu .el-submenu__title{
        color: #fff;
    }
    .el-menu--horizontal .el-submenu .el-submenu__title:hover{
        background: url(../../../static/img/tooplate_menu_item_r.png) right no-repeat;
    }
    .el-menu--horizontal .el-submenu>.el-menu{
        background-color: #AF4F25;
    }
    .el-menu--horizontal .el-submenu .el-menu-item{
        background-color: #AF4F25;
    }
</style>
