

## Local development ##

	// Open server and access http://localhost:8080 in browser
	npm run dev

## Constructing production ##

	// Constructing project
	npm run build
##  less 编译  songsongs##

第一步：

安装less依赖，npm install less less-loader --save

第二步：

修改webpack.config.js文件，配置loader加载依赖，让其支持外部的less,在原来的代码上添加

{

test: /\.less$/,

loader: "style-loader!css-loader!less-loader",

},
现在基本上已经安装完成了，然后在使用的时候在style标签里加上lang=”less”里面就可以写less的代码了(style标签里加上 scoped 为只在此作用域 有效)

（或者@import './index.less'; //引入全局less文件）。