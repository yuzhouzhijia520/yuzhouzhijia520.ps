<template>
    <div class="myBlog">
          <el-collapse v-model="activeName" accordion>
            <el-collapse-item class="item titleBlog" title="MyBlog 'Markown-it' Test" name="1">
                <p id="PSmarkdownText"></p>
                <div v-html='PSmarkdownText'></div>
                <div>在界面中一致：所有的元素和结构需保持一致，比如：设计样式、图标和文本、元素的位置等。</div>
            </el-collapse-item>
             <el-collapse-item class="titleBlog" title="MyBlog 'babel-polyfill'" name="2">
                <div v-html='PSmarkdownText'></div>
                <div>https://babeljs.io/docs/usage/polyfill/</div>
            </el-collapse-item>
        </el-collapse>

    </div>
</template>

<script>
import marked from 'marked';
  export default {
    data() {
      return {
          activeName: '1',
          PSmarkdownText:"songsongs is blog"
      }
    },
    mounted(){
        let _this=this;
            _this.PSmarkdownText = marked('# markdown-it rulezz!');
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
                    color: aliceblue;
                    border-radius: 50px;
                }
            }
            
        }
    }
}

</style>