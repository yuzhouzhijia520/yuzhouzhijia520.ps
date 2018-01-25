<template>
    <div class="myBlog">
          <el-collapse v-model="activeName" accordion>
            <el-collapse-item class="item titleBlog" title="1、前端知识体系汇总" name="1">
                <p id="PSmarkdownText"></p>
                <div v-html='PSmarkdownText1' class='markdown-body'></div>
            </el-collapse-item>
             <el-collapse-item class="titleBlog" title="2、Blog" name="2">
                <div v-html='PSmarkdownText2' class='markdown-body'></div>
            </el-collapse-item>
        </el-collapse>

    </div>
</template>

<script>
    import '../page/styles/styles.css';
    import marked from '../../../static/marked/marked.js';
  export default {
    data() {
      return {
          activeName: '1',
          PSmarkdownText1:"",
          PSmarkdownText2:""
      }
    },
    methods(){
    },
    mounted(){
        let _this=this;
        $.get('../../../static/marked/markdown/BlogWeb1.md').done((res)=>{
                    _this.PSmarkdownText1 = marked(res);
        });
        $.get('../../../static/marked/markdown/BlogWeb2.md').done((res)=>{
                    _this.PSmarkdownText2 = marked(res);
        });   
    }
  }
</script>
<style  lang="less">
.myBlog{
    .el-collapse{
        border: 1px solid #237b18;
        border-radius: 50px;
        padding: 10px 0;
       .titleBlog{
           .el-collapse-item__header{
                background-color: transparent;
                border-bottom: 0;
                color:#4bea4a;
            }
            .el-collapse-item__wrap{
                background-color: transparent;
                border-bottom: 0;
                .el-collapse-item__content{                    
                    border-radius: 50px;
                }
            }
            
        }
    }
}

</style>