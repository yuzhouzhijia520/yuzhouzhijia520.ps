<template>
    <div class="myBlog">
          <el-collapse v-model="activeName" accordion>
            <el-collapse-item class="item" title="MyBlog 'Markown-it' Test" name="1">
                <p id="PSmarkdownText"></p>
                <div>{{PSmarkdownText}}</div>
                <div>在界面中一致：所有的元素和结构需保持一致，比如：设计样式、图标和文本、元素的位置等。</div>
            </el-collapse-item>
             <el-collapse-item title="MyBlog 'babel-polyfill'" name="2">
                <div>{{PSmarkdownText}}</div>
                <div>https://babeljs.io/docs/usage/polyfill/</div>
            </el-collapse-item>
        </el-collapse>

    </div>
</template>

<script>
  export default {
    data() {
      return {
          activeName: '1',
          PSmarkdownText:"songsongs is blog"
      }
    },
    mounted(){
        let _this=this;
        let MarkdownIt = require('markdown-it');
        let   md = new MarkdownIt();
            _this.PSmarkdownText = md.render('# markdown-it rulezz!');
            let mar=document.getElementById('PSmarkdownText');
           // mar.innerHtml=md.render('# markdown-it rulezz!');
           mar.innerHtml="<strong>设置标签的html内容</strong>";
    },
    methods: {
        
    }
  }
</script>
<style scoped lang="less">
.myBlog{
    .el-collapse{
        .el-collapse-item.item.is-active{
           .el-collapse-item__header{
              background-color: transparent;
            }
            
        }
    }
}

</style>