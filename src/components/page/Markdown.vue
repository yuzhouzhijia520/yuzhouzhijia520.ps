<template>
    <div>
        <div class="crumbs">
            <el-breadcrumb separator="/">
                <el-breadcrumb-item><i class="el-icon-date"></i> 表单</el-breadcrumb-item>
                <el-breadcrumb-item>markdown</el-breadcrumb-item>
            </el-breadcrumb>
        </div>
        <div class="plugins-tips">
           Markdown文件解析测试
        </div>
        <div class="plugins-tips">
           <div class="plugins-content markdown-body" v-html='mdContent'>
           </div>
        </div>
    </div>
</template>

<script>
    import './styles/styles.css';
    import marked from '../../../static/marked/marked.js';
    export default {
        data: function(){
            return {
                content:'',
                configs: {
                    status: true,
                    initialValue: '',
                    renderingConfig: {
                        codeSyntaxHighlighting: true,
                        highlightingTheme: 'atom-one-light'
                    }
                },
                mdContent:``
            }
        },
        methods:{
            getMarkdownss(){
                let _this=this;
                $.get('../../../static/marked/markdown/README.md').done((res)=>{
                    _this.mdContent=marked(res);
                });
            }
        },
        mounted(){
            let _this=this;
            _this.getMarkdownss();
          
        }
    }
</script>