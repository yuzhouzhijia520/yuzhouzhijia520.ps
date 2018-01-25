##  1、行内元素有哪些？块级元素有哪些？ 空(void)元素有那些？    
* 首先：CSS规范规定，每个元素都有display属性，确定该元素的类型，每个元素都有默认的display值，如div的display默认值为“block”，则为“块级”元素；span默认display属性值为“inline”，是“行内”元素。

* （1）行内元素有：
```
                 a span img input select strong textarea（强调的语气）
```
* （2）块级元素有：
```
                  div form table ul ol li dl dt dd h1 h2 h3 h4…p
```
* （3）常见的空元素：
```
                  <br> <hr> <img> <input> <link> <meta>
```
*   不同浏览器（版本）略有不同。     

## 2、介绍一下你对浏览器内核的理解？
* 主要分成两部分：渲染引擎(layout engineer或Rendering Engine)和JS引擎。
* 渲染引擎：负责取得网页的内容（HTML、XML、图像等等）、整理讯息（例如加入CSS等），以及计算网页的显示方式，然后会输出至显示器或打印机。浏览器的内核的不同对于网页的语法解释会有不同，所以渲染的效果也不相同。所有网页浏览器、电子邮件客户端以及其它需要编辑、显示网络内容的应用程序都需要内核。
* JS引擎则：解析和执行javascript来实现网页的动态效果。

* 最开始渲染引擎和JS引擎并没有区分的很明确，后来JS引擎越来越独立，内核就倾向于只指渲染引擎。

## 3、常见的浏览器内核有哪些？
* 浏览器的内核是分为两个部分的，一是渲染引擎，另一个是JS引擎。现在JS引擎比较独立，内核更加倾向于说渲染引擎。

* 1、Trident内核：代表作品是IE，因IE捆绑在Windows中，所以占有极高的份额，又称为IE内核或MSHTML，此内核只能用于Windows平台，且不是开源的。
代表作品还有腾讯、Maxthon（遨游）、360浏览器等。但由于市场份额比较大，曾经出现脱离了W3C标准的时候，同时IE版本比较多，存在很多的兼容性问题。
* 2、Gecko内核：代表作品是Firefox，即火狐浏览器。因火狐是最多的用户，故常被称为firefox内核它是开源的，最大优势是跨平台，在Microsoft Windows、Linux、MacOs X等主要操作系统中使用。
*  Mozilla是网景公司在第一次浏览器大战败给微软之后创建的。有兴趣的同学可以了解一下浏览器大战
* 3、Webkit内核：代表作品是Safari、曾经的Chrome，是开源的项目。
* 4、Presto内核：代表作品是Opera，Presto是由Opera Software开发的浏览器排版引擎，它是世界公认最快的渲染速度的引擎。在13年之后，Opera宣布加入谷歌阵营，弃用了Presto 
* 5、Blink内核：由Google和Opera Software开发的浏览器排版引擎，2013年4月发布。现在Chrome内核是Blink。

## 4、display有哪些值？说明他们的作用。
    block       	块类型。默认宽度为父元素宽度，可设置宽高，换行显示。
    none        	缺省值。象行内元素类型一样显示。
    inline      	行内元素类型。默认宽度为内容宽度，不可设置宽高，同行显示。
    inline-block  默认宽度为内容宽度，可以设置宽高，同行显示。
    list-item   	象块类型元素一样显示，并添加样式列表标记。
    table       	此元素会作为块级表格来显示。
    inherit     	规定应该从父元素继承 display 属性的值。

## 5、position的值relative和absolute定位原点是？
    absolute
  	生成绝对定位的元素，相对于值不为 static的第一个父元素进行定位。
    fixed （老IE不支持）
  	生成绝对定位的元素，相对于浏览器窗口进行定位。
    relative
  	生成相对定位的元素，相对于其正常位置进行定位。
    static
  	默认值。没有定位，元素出现在正常的流中（忽略 top, bottom, left, right z-index 声明）。
    inherit
  	规定从父元素继承 position 属性的值。

## 6、css定义的权重
以下是权重的规则：标签的权重为1，class的权重为10，id的权重为100，以下例子是演示各种定义的权重值：

  /*权重为1*/
  div{
  }
  /*权重为10*/
  .class1{
  }
  /*权重为100*/
  #id1{
  }
  /*权重为100+1=101*/
  #id1 div{
  }
  /*权重为10+1=11*/
  .class1 div{
  }
  /*权重为10+10+1=21*/
  .class1 .class2 div{
  }

  如果权重相同，则最后定义的样式会起作用，但是应该避免这种情况出现

## 7、请解释一下为什么需要清除浮动？清除浮动的方式
* 详情见 <a href="https://www.cnblogs.com/nxl0908/p/7245460.html">Link</a>
* 清除浮动是为了清除使用浮动元素产生的影响。浮动的元素，高度会塌陷，而高度的塌陷使我们页面后面的布局不能正常显示。
* 1、父级div定义height；
* 2、父级div 也一起浮动；
* 3、常规的使用一个class；
  	.clearfix::before, .clearfix::after {
  	    content: " ";
  	    display: table;
  	}
  	.clearfix::after {
  	    clear: both;
  	}
  	.clearfix {
  	    *zoom: 1;
  	}

* 4、SASS编译的时候，浮动元素的父级div定义伪类:after
  	&::after,&::before{
  	    content: " ";
          visibility: hidden;
          display: block;
          height: 0;
          clear: both;
  	}

* 解析原理：
* 1) display:block 使生成的元素以块级元素显示,占满剩余空间;
* 2) height:0 避免生成内容破坏原有布局的高度。
* 3) visibility:hidden 使生成的内容不可见，并允许可能被生成内容盖住的内容可以进行点击和交互;
* 4）通过 content:"."生成内容作为最后一个元素，至于content里面是点还是其他都是可以的，例如oocss里面就有经典的 content:".",有些版本可能content 里面内容为空,一丝冰凉是不推荐这样做的,firefox直到7.0 content:”" 仍然会产生额外的空隙；
* 5）zoom：1 触发IE hasLayout。

* 通过分析发现，除了clear：both用来闭合浮动的，其他代码无非都是为了隐藏掉content生成的内容，这也就是其他版本的闭合浮动为什么会有font-size：0，line-height：0。

## 8、如果需要手动写动画，你认为最小时间间隔是多久，为什么？
多数显示器默认频率是60Hz，即1秒刷新60次，所以理论上最小间隔为1/60＊1000ms ＝ 16.7ms

## 9、同步和异步的区别?
* 同步的概念
同步，我的理解是一种线性执行的方式，执行的流程不能跨越。一般用于流程性比较强的程序，我们做的用户登录功能也是同步处理的，必须用户通过用户名和密码验证后才能进入系统的操作。

* 异步的概念
异步，是一种并行处理的方式，不必等待一个程序执行完，可以执行其它的任务。在程序中异步处理的结果通常使用回调函数来处理结果。在JavaScript中实现异步的方式主要有Ajax和H5新增的Web Worker。
同步强调的是顺序性.谁先谁后.异步则不存在这种顺序性.

## 10、如何解决跨域问题?
cors、jsonp、window.name、location.hash、csst、代理、document.domain、window.postMessage、flash等（详情待整理）

## 11、你有用过哪些前端性能优化的方法？
 见<a href="https://github.com/yuzhouzhijia520/ps-note/blob/master/8%E3%80%81Web%E5%89%8D%E7%AB%AF%E6%80%A7%E8%83%BD%E4%BC%98%E5%8C%96.md">Web前端性能优化</a>

## 12、一个页面从输入 URL 到页面加载显示完成，这个过程中都发生了什么？
    详细版：
  	1、浏览器会开启一个线程来处理这个请求，对 URL 分析判断如果是 http 协议就按照 Web 方式来处理;
  	2、调用浏览器内核中的对应方法，比如 WebView 中的 loadUrl 方法;
    3、通过DNS解析获取网址的IP地址，设置 UA 等信息发出第二个GET请求;
  	4、进行HTTP协议会话，客户端发送报头(请求报头);
    5、进入到web服务器上的 Web Server，如 Apache、Tomcat、Node.JS 等服务器;
    6、进入部署好的后端应用，如 PHP、Java、JavaScript、Python 等，找到对应的请求处理;
  	7、处理结束回馈报头，此处如果浏览器访问过，缓存上有对应资源，会与服务器最后修改时间对比，一致则返回304;
    8、浏览器开始下载html文档(响应报头，状态码200)，同时使用缓存;
    9、文档树建立，根据标记请求所需指定MIME类型的文件（比如css、js）,同时设置了cookie;
    10、页面开始渲染DOM，JS根据DOM API操作DOM,执行事件绑定等，页面显示完成。

    简洁版：
  	浏览器根据请求的URL交给DNS域名解析，找到真实IP，向服务器发起请求；
  	服务器交给后台处理完成后返回数据，浏览器接收文件（HTML、JS、CSS、图象等）；
  	浏览器对加载到的资源（HTML、JS、CSS等）进行语法解析，建立相应的内部数据结构（如HTML的DOM）；
  	载入解析到的资源文件，渲染页面，完成。
    
## 13、HTML、XML、XHTML 有什么区别?
* HTML，超文本标记语言，是语法较为松散的、不严格的Web语言；
* XML，可扩展标记语言，主要用于存储数据和结构，可扩展；
* XHTML，可扩展超文本标记语言，基于XML，作用与HTML类似，但语法更严格。

## 14、模块化开发怎么做？
* 立即执行函数,不暴露私有成员
```
var module1 = (function(){
     　　　　var _count = 0;
     　　　　var m1 = function(){
     　　　　　　//...
     　　　　};
     　　　　var m2 = function(){
     　　　　　　//...
     　　　　};
     　　　　return {
     　　　　　　m1 : m1,
     　　　　　　m2 : m2
     　　　　};
     　　})();
```
## 15、考察立即执行函数
```
(function(){
     　　　　console.log(this);
     　　})();
 result:undefined
```
