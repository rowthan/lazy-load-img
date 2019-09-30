
 [![npm](https://img.shields.io/npm/v/lazy-load-img.svg?style=flat-square)](https://www.npmjs.com/package/lazy-load-img) [![npm](https://img.shields.io/npm/dt/lazy-load-img.svg?style=flat-square)](https://www.npmjs.com/package/lazy-load-img) 


### 安装
```
npm install lazy-load-img --save
```
vue使用，请移动至[vue-lazy-load-img](https://github.com/lzxb/vue-lazy-load-img)

### 优势
```
1.原生js开发，不依赖任何框架或库
2.支持将各种宽高不一致的图片，自动剪切成默认图片的宽高
  比如说你的默认图片是一张正方形的图片，则各种宽度高度不一样的图片，自动剪切成正方形。
  完美解决移动端开发中，用户上传图片宽高不一致而导致的图片变形的问题
3.简洁的API，让你分分钟入门！！！
```


### 默认模式
```javascript
  var lazyLoadImg = new LazyLoadImg();
```

#### 效果演示
[![demo](https://github.com/lzxb/lazy-load-img/raw/master/shot/mode-default.png)](http://lzxb.github.io/lazy-load-img/examples/mode-default.html)

### 自定义模式
```javascript
  var lazyLoadImg = new LazyLoadImg({
      el: document.querySelector('#list'),//对象范围，位于该节点下的图片才会采用懒加载的方式。默认为body
      mode: 'diy', //默认模式，将显示原图，diy模式，将自定义剪切，默认剪切居中部分
      time: 300, // 设置一个检测时间间隔
      complete: true, //页面内所有数据图片加载完成后，是否自己销毁程序，true默认销毁，false不销毁
      errorImage:"./images/error.png",//定义加载失败的默认图片
      position: { // 只要其中一个位置符合条件，都会触发加载机制
          top: 0, // 元素距离顶部
          right: 0, // 元素距离右边
          bottom: 0, // 元素距离下面
          left: 0 // 元素距离左边
      },
      diy: { //设置图片剪切规则，diy模式时才有效果
          backgroundSize: 'cover',
          backgroundRepeat: 'no-repeat',
          backgroundPosition: 'center center'
      },
      before: function () {

      },
      success: function (el) {
          el.classList.add('success')
      },
      error: function (el) {
          console.log("error message")
      }
  })

  // lazyLoadImg.start() // 重新开启懒加载程序
  // lazyLoadImg.destroy() // 销毁图片懒加载程序
``` 

#### 效果演示
 [![demo](https://github.com/lzxb/lazy-load-img/raw/master/shot/mode-diy.png)](http://lzxb.github.io/lazy-load-img/examples/mode-diy.html)

### changelog
* 默认选取目标为body标签下所有图片
* 新增errorImage 参数，供用户自定义加载失败的路径
* 新增加载报告（console控制台打印）
* 新增了一些注释
* 新增complete()钩子函数

#### TODO
- [ ] 图片加载高度不同导致在加载过程中dom跳动，为解决图片导致页面元素跳动，对图片初始化时高度设置为目标图片高度、宽度一致。
- [ ] img元素高度为auto(0)时，不能检测其可视
- [ ] 取消使用timer模式检测，使用scroll，并增加hover检测（用户滚动展示元素）
