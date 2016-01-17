## webpack学习笔记

#### 1. webpack是什么?

 webpack是一个模块打包工具，通过依赖处理模块，并生成那些模块静态资源。webpack把所有的资源（js，css和图片等）都当做是模块——webpack中可以引用css，css中可以嵌入图片dataUrl，对于不同类型的资源，webpack有对应的模块加载器。webpack模块打包器会分析模块间的依赖关系，最后 生成了优化且合并后的静态资源。

官网:[https://webpack.github.io/](https://webpack.github.io/)

#### 2. webpack.config.js常见配置


- 一个最简单的配置

 ```
 // webpack.config.js
module.exports = {
  entry: './main.js',
  output: {
    filename: 'bundle.js'
  },
  module: {
    //定义加载器
    loaders: [
      { test: /\.coffee$/, loader: 'coffee-loader' },
      {
        test: /\.js$/,
        loader: 'babel-loader',
        query: {
          presets: ['es2015', 'react']
        }
      }
    ]
  }
};
 ```

- 调用`require`时省略后缀的方法,添加`resolve.extensions`

	```
	 resolve: {
    // you can now require('file') instead of require('file.coffee')
    extensions: ['', '.js', '.json', '.coffee']
   }
	```

- Multiple entrypoints

  假设你有两个页面A、B，你肯定不希望用户浏览A页面的时候下载了B页面的代码。这时候你可以使用
  `multiple entrypoints`特性

	```
	// webpack.config.js
module.exports = {
  entry: {
    A: './a.js',
    B: './b.js'
  },
  output: {
    path: 'build',
    filename: '[name].js' // Template based on keys in entry above
  }
};

	```

当执行`webpack`命令时，就会在build目录下生成a.js和b.js,所以你可以在html页面中根据需要引用:

```
<script src="build/a.js"></script>
```

- 优化公共代码


	 ```
	 // webpack.config.js

	var webpack = require('webpack');

	var commonsPlugin =
	  new webpack.optimize.CommonsChunkPlugin('common.js');

	module.exports = {
	  entry: {
	    Profile: './profile.js',
	    Feed: './feed.js'
	  },
	  output: {
	   // Make sure to use [name] or [id] in output.filename
      //  when using multiple entry points
	    path: 'build',
	    filename: '[name].js' // Template based on keys in entry above
	  },
	  plugins: [commonsPlugin]
	};

	 ```
  现在你只需要在引用的地方多加一个`common.js`,`<script src="build/common.js"></script>`.



#### 3. webpack使用

#### 4. webpack dev server

webpack-dev-server是一个轻量级的node.js服务器，同webpack，webpack-dev-server也可以分析模块的依赖关系进行打包——webpack命令的所有选项对webpack-dev-server命令都有效。但不同的是，webpack-dev-server不会在本地目录下生成目标文件，而是放在内存里，通过访问服务器相应地址获取。另外，webpack-dev-server自带有一个轻量级的runtime，浏览器可以通过Socket.IO与服务器连接，服务器向客户端浏览器送编译状态信息，然后客户端/浏览器根据这些信息做相应的处理，如：刷新，模块热替换等。

#### 5. 学习资料

 - [webpack howto](https://github.com/petehunt/webpack-howto)
 - [webpack学习笔记](http://blog.csdn.net/zhbhun/article/details/47208885)
 - [webpack gitbook](https://fakefish.github.io/react-webpack-cookbook/)
