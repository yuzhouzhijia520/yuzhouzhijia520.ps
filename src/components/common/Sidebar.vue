<template>
    <div class="sidebar">
        <el-menu :default-active="onRoutes" class="el-menu-vertical-demo" theme="dark" unique-opened router>
            <template v-for="item in items">
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
        width: 250px;
        left: 0;
        top: 70px;
        bottom:0;
    }
    .sidebar > ul {
        height:100%;
        .el-menu{

                   background-color: transparent !important;

            }
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
</style>
