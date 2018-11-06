# CSS
## 布局

**水平居中**

 方法一： 定宽 + margin: 0 auto

```
<div class="parent">
       <p class="child">我是子元素</p>
</div>

<style>
.child{
    width: 100px;
    margin: 0 auto;
}
</style>
```

 方法二： 行内元素 inline-block + text-align

 ```
<div class="txtCenter">xxx</div>
<div class="imgCenter"><img src="xxx" /></div>

<style>
div.txtCenter{
	text-align:center;
}
.imgCenter{
    text-align:center; 
}
</style>
 ```

 方法三： display: table + margin: 0 auto
```
<div class="parent">
       <p class="child">我是子元素</p>
</div>

<style>
.parent{
    display:table;
}
.child{
    margin: 0 auto;
}
</style>
```
 方法四： 父元素display: flex + justify-content: center
```
<div class="parent">
       <p class="child">我是子元素</p>
</div>

<style>
.parent{
    display:flex;/*Flex布局*/
    display: -webkit-flex; /* Safari */
    justify-content: center;/*指定水平居中*/
}
</style>

```

**垂直居中**

 方法一： display: table-cell + vertical-align: middle
```
<div class="parent">
       <p class="child">我是子元素</p>
</div>

<style>
.parent {
    display: table;
}
.child {
    display: table-cell;
    vertical-align: middle;
}
</style>
```
 方法二： 父元素display: flex + align-item: center
```
<div class="parent">
       <p class="child">我是子元素</p>
</div>

<style>
.parent{
    display:flex;/*Flex布局*/
    display: -webkit-flex; /* Safari */
    align-items:center;/*指定垂直居中*/
}
</style>
```
方法三：对单行文本使用 line-height
```
<div class="parent">xxx</div>

<style>
.parent{
    height: 300px;
    line-height: 300px;
}
</style>
```

方法四： 对图片使用 line-height + vertical-align

```
<div class="parent">
       <img src="xxx"/>
</div>

<style>
.parent{
    height: 300px;
    line-height: 300px;
}
img{
    vertical-align: middle;
}
</style>
```

方法五： 绝对定位 margin: auto 0
```
<div class="parent">
       <p class="child">我是子元素</p>
</div>

<style>
.parent {
    position: relative;
}
.child {
    position: absolute;
    top: 0;
    bottom: 0;
    margin: auto 0;
}
</style>
```

**🌞居中万金油**

方法：position: absolute + top + left + transform: translate()
```
<div class="parent">
       <div class="child">xxx</div>
</div>

<style>
.parent{
    position: relative;
}
.child{
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}
</style>
```
**图片文字对齐**

 方法一： 图片作为背景图片 background-image background-repeat background-size
```
<div class="testTXT">
	<span>XXXX</span>
</div>

<style>
.testTXT {
    height:60px;
    line-height:60px;
    padding-left:65px;
    background:url(xxx) no-repeat left center
}
</style>
```

 方法二： 图片固定宽高，父容器相对定位，子容器绝对定位

```
<div class="img">
    <img src="xxx" />
</div>

<style>
.img {
    border: 1px solid black;
    width: 200px;
    height: 200px;
    position: relative;
}

.img img {
    width: 100px;
    height: 100px;
    position: absolute;
    top: 50%;
    left: 50%;
    margin: -50px 0 0 -50px;
}
</style>
```

 方法三： 图片宽高自适应，使用line-height，text-align，vertical-align，max-width,max-height

```
<div class="img">
    <img src="xxx" />
</div>

<style>
.img {
    border: 1px solid black;
    width: 200px;
    height: 200px;
    line-height: 200px;
    text-align: center;
}

.img img {
    max-width: 150px;
    max-height: 150px;
    vertical-align: middle;
}
</style>
```
 方法四： css3 display:box
```
<div class="img">
    <img src="xxx" />
    <span>xxx</span>
</div>

<style>
.img {
    border: 1px solid black;
    width: 200px;
    height: 200px;
    text-align: center;
    display: -webkit-box;
    -webkit-box-align: center;
    -webkit-box-pack: center;
    display: -moz-box;
    -moz-box-align: center;
    -moz-box-pack: center;
    display: -o-box;
    -o-box-align: center;
    -o-box-pack: center;
    display: -ms-box;
    -ms-box-align: center;
    -ms-box-pack: center;
    display: box;
    box-align: center;
    box-pack: center;
}

.img img {
    width: 100px;
    height: 100px;
}
</style>
```

> 参考文章
> 
> [完美实现文字图片水平垂直居中](https://segmentfault.com/a/1190000004149988)

**多列布局**

方法一： float + overflow: hidden

方法二： columns-width columns-count（IE10以下不支持，需要添加前缀）

方法三： flex （也需要加入兼容语法）

> 参考文章
>
> [CSS布局之多列布局](https://blog.csdn.net/wangwangwanglichao/article/details/79765161)

**圣杯布局 && 双飞翼布局**

> 参考文章
>
> [圣杯布局、双飞翼布局、Flex布局和绝对定位布局的几种经典布局的具体实现示例](https://blog.csdn.net/wangchengiii/article/details/77926868)


## 定位
absolute 
* 脱离文档流，相对于已定位的父元素进行移动，当某个absolute定位元素的父元素具有position:relative/absolute/fixed时，定位元素都会依据父元素而定位，而父元素没有设置position属性或者设置了默认属性，那么定位属性会依据html元素来定位

relative 
* 相对于自身位置移动，原位置还保留在文档流中，内容发生了移动

fixed 
* 脱离文档流，相对于浏览器窗口，对于IE78需要DOCTYPE

static 
* position的默认值

sticky 
* 粘性定位 必须设置上下左右其中一个值（达到阈值前会相对定位，达到后变成固定定位）
* 挺好玩的，例如导航条什么的可以用上
* 但是兼容性非常不乐观

z-index
* 只对于relative/absolute/fixed三种定位有效
* 父子元素设置z-index无法进行比较，但是可以通过设置子元素的z-index为负数来控制顺序

## 盒子模型
盒子模型 = content + padding + border + margin 

盒子模型分为两种：

标准盒子 width = content

![](./assets/standardbox.jpeg)

IE盒子 width = content + padding + border

![](./assets/iebox.jpeg)


css3新属性——box-sizing

* 默认值 box-sizing: content-box

* box-sizing: content-box 设定的width只含内容宽度，不包括padding + border（相当于标准盒子）
* box-sizing: border-box 设定的width包括content + padding + border （相当于IE盒子）
* 在IE8，box-sizing的值为border-box时，不能与min-width, max-width, min-height或max-height的一起使用，因为IE8对min-和max-的解析，仍是作用于content-box，不受box-sizing属性控制
* 一般都直接全局设置 `*{box-sizing: border-box}`
* 兼容ff和移动端的话最好加上前缀`-moz-`,`-webkit-`
``` 
*, *:before, *:after {
　　-moz-box-sizing: border-box;
　　-webkit-box-sizing: border-box;
　　box-sizing: border-box;
　　}
```
* 对于行级元素inline，margin-top和margin-bottom对于上下元素无效，margin-left和margin-right有效

* 对于相邻的块级元素block，margin-bottom和margin-top 
    * 若都是正数，取最大值
    * 若都是负数，取最小值
    * 一正一负，正负相加
>参考文章
>
> [border-box和content-box最直观的区别和解释【不理解包赔】](https://blog.csdn.net/andynikolas/article/details/79169798
)

## 样式引入方式

link标签
* 没有兼容性问题

* 还可以引入图标等资源
* 在页面加载的时候同时加载css文件
* 可通过js控制dom操作样式

import引入
* 兼容性问题 css2.1以下 IE5以下 不支持

* 网页加载完后再加载css文件，所以会出现闪烁现象
* 不可通过js修改样式
* 只能引入样式文件，但是可以在css文件里再引入css文件
* 推荐书写 @import url(style.css)

## 块与内联
块状元素
* 特点
    * 独占一行

    * 宽高边距都可控
    * 宽度默认父容器宽度
    * 可容纳块与内联
* 元素
    * div

    * p
    * h
    * ul
    * dl
    * ol
    * form

内联元素
* 特点
    * 都在一行

    * 高，行高，上下内外边距不可改，左右内外边距可改变
    * 宽度是内容宽度
    * 只能容纳内联和文本
* 元素
    * a

    * span
    * input
    * img
    * textarea

## BFC
块级格式化上下文

触发条件
* float不为none

* overflow不为visible
* display 为table-cell，table-caption，inline-block
* position为absolute，fixed
* fieldset元素

功能
* 自我独立，内部元素不会影响外部元素

* 会包含浮动元素
* 同一个bFC的margin重叠

## 浮动

**浮动**

> 参考文章
> 
> [CSS浮动float详解](https://www.jianshu.com/p/07eb19957991)

**清除浮动**

原因
* 浮动元素脱离文档流，影响页面结构
* 父元素高度无法撑开

```
.clearfix {
    zoom: 1;
}

.clearfix::after {
    content: '';
    clear: both;
    height: 0;
    visibility: hidden;
    display: block;
}
```
## 伪类元素:before
* ::before 和 :before 差别时前者是css3调整的写法，所以后者的兼容性更好，其实效果一样

* 必须与content属性一起使用
* 不能通过js控制，只能在css中使用
* 用途：清除浮动，制造各种小形状，icon

## flex & gird

**flex**

父容器属性
* display: flex

* flex-direction 方向
* flex-wrap 是否尾随换行
* flex-flow: <flex-direction> || <flex-wrap>
* justify-content 父容器水平设置
* align-items 子容器垂直设置
* align-content 父容器垂直设置

子容器属性
* order 排列顺序

* flex-grow 分配剩余空间
* flex-shrink 缩小
* flex-basis 分配剩余空间之前，子容器宽度
* flex: <flex-grow> <flex-shrink>? || <flex-basis> 默认 0 1 auto

> 参考文章
> 
> [A Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)

**grid**

> 参考文章
> 
> [CSS：Grid 布局](https://juejin.im/entry/5894135c8fd9c5a19507f6a1)

## 可继承属性

可继承属性
* 字体属性font

* visibility
* cursor
* color
* 部分文本属性
    * line-height

    * word-spacing字间距
    * letter-spacing字符间距
    * text-transform大小写
    * direction方向
    * 其中文本缩进text-indent，text-align只有块状元素可继承

不可继承属性
* 背景属性background

* 布局属性margin
* 定位属性position
* display
* 部分文本属性
    * vertical-align

    * text-decoration
    * text-shadow
    * white-space

## CSS3
边框图片，圆角
* border-radius

* border-image

背景
* background-image

* background-size
* background-origin（位置区域content-box/border-box/padding-box）
* background-clip（裁剪描绘区域）
* 多重背景

渐变色
* Linear-gradient(angle,color1 10%,color2 30%,..)

* Radial-gradient
* 兼容性，添加前缀

文本效果
* Text-shadow

* box-shadow
* Text-overflow
* Word-wrap (break-word,强制断开分行）
* Word-break（keep-all,break-all 是否换行）
* 一行省略
```
display: block;
text-overflow: ellipsis;
white-space: nowrap;
overflow: hidden;
```
* N行省略
```
display: -webkit-box;
overflow: hidden;
text-overflow: ellipsis;
-webkit-box-orient: vertical;
-webkit-line-clamp: n;
```

transform
* Matrix 矩阵变换

* translate平移
* scale缩放
* rotate旋转
* skew倾斜

过渡 transition
* transition-property css属性，列表以逗号分隔

* transition-duration 过渡时间
* transition-timing-function 时间曲线
* transition-delay 延迟时间

动画

@keyframes
* 动画名

* 动画时长百分比 或者 from to
* 每个对应的css样式
```
@keyframes mymove
{
    0%   {top:0px;}
    25%  {top:200px;}
    50%  {top:100px;}
    75%  {top:200px;}
    100% {top:0px;}
}
```

animation
* animation-name 对应的keyframes

* animation-duration 动画时间
* animation-timing-function 时间曲线
* animation-delay 延迟时间
* animation-iteration-count 播放次数
* animation-direction 是否轮流反向播放
## 单位
px

em 当前字体大小

rem 根节点字体大小

vh, vw, vmin, vmax 视窗单位

ex, ch 给予特殊字体的单位
* ex em的一半，字体的中间标志，可以上下用于微调

* ch 数字0的宽度

fr
* 用于grid布局，自由空间分配

## BEM / 命名空间
> 参考文章
> 
> [【CSS模块化之路1】使用BEM与命名空间来规范CSS](https://juejin.im/post/5b20e8e0e51d4506c60e47f5)

## 响应式设计
* rem适应屏幕大小

* 媒体查询
```
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no”/>
```
```
@media (max-width: 960px) and (min-width: 600px) {…}
```
* flex流式布局
* 响应式图片<picture>

## CSS变量
> 参考文章
> 
> [关于 CSS 变量，你需要了解的一切](https://mp.weixin.qq.com/s/wFz0PsOGaLb9KDGfEJuLaA)

## CSS选择器及其解析顺序
CSS选择器分类
* \*

* .class
* #id
* div
* div,p
* div p
* div>p
* div+p
* [attribute]
* [attirbute=‘123']
* [attribute~=‘123’]
* [attritube|=‘123’]
* :link :hover :active :visited :focus
* :before :after
* p:first-of-type (last, only，nth(n)) 其父元素的第1/最后/唯一/n个p元素的所有元素
* p:nth-（-last-）child(n) 其父元素的（顺序，倒序）第n个元素的所有p元素
* :root
* p:empty
* :disabled :checked
* :not(p)

优先级排序
* 计算法则
    * 元素选择器： 1

    * 类选择器：10
    * ID选择器：100
    * 内联： 1000
* !important > 行内样式>ID选择器 > 类选择器 > 标签 > 通配符 > 继承 > 浏览器默认属性

## CSS优化
* 雪碧图，利用背景图片位移

* 对类名的设计与选择
    * 避免不必要的重复

    * 避免！important
    * 避免链式，后代选择符
* 预处理
    * less，sass
* 后处理
    * postCSS

## 视差滚动
> 参考文章
> 
> [[译] 高性能视差滚动](https://juejin.im/entry/5975ede7f265da6c322e213f)
> 
> [demo](https://googlechromelabs.github.io/ui-element-samples/parallax/)
> 
> [Pure CSS Parallax Websites](https://keithclark.co.uk/articles/pure-css-parallax-websites/)

# HTML
# JS
## 基础
### 基础类型
### 引用类型
### 类型比较

## 核心
### 创建对象
### 继承
### 原型
### 原型链
### call/apply/bind
### this
### 闭包
### 对象拷贝

## ES6
### let const
### 箭头函数
### class
### Set Map
### decorator
### proxy

## EventLoop
### 异步队列
#### 微任务
#### 宏任务

## 异步Ajax
### XHR
### callback
### promise
### async/await
### 第三方库

## 经典函数
### 防抖
### 节流

## 设计模式
### 单例模式
### 工厂模式
### 享元模式
### 订阅者/发布者模式
### 装饰器/适配器模式
### 代理模式

# Web API
## DOM
## bOM
## canvas WebGL
## worker
## geolocation

# 事件
## 事件捕捉/冒泡/委托
## 自定义事件
## 点击事件
## 拖拽事件

# 网络
## TCP/IP
## HTTP
### HTTP基础
#### HTTP头部
#### HTTP连接过程
#### GET vs POST
### HTTP缓存
#### 强缓存
#### 协商缓存
### HTTP状态码
### HTTP/2.0
## HTTPS
## 网络安全
### 攻击类型
#### XSS
#### CSRF
#### DDos
#### SGL注入
#### SYN攻击
### 防御措施
#### CSP
#### HSTS

# 浏览器
## 浏览器渲染过程
## V8
## 浏览器存储
## 跨域
### JSONP
### CORS
### iframe
### 反向代理

# 性能优化
## RAIL
### Response
### Animation
### Idle
### Load
#### 网络层面
##### 请求优化
##### 减少请求
#### 渲染层面
##### SSR
##### 浏览器渲染
##### DOM
##### 首屏优化
## SEO
## 性能监控

# 前端框架
## Vue
### Vue
#### 数据双向绑定
#### 生命周期
#### 异步更新
#### 虚拟DOM
### Vue Router
### VueX
### Vue SSR
## React
### React
### React Router
### Redux/Mobx
### RN

# 多端模式
## 移动端
### JSbridge
## 桌面端
## Eletron

# 构建打包工具
## Webpack
### 基本配置
### Loader
### Plugins

# 其他工具
## 类型检查
### TS
### flow
## 测试
## 模块化&babel
## 语法检查

# 调试工具
## 浏览器调试
## 模拟器调试
## 真机调试

# 发布
## 持续集成
## 服务器
## 错误监控
## 统计

# 算法与数据结构
## 算法
### 排序
## 数据结构
### 链表
### 队列
### 栈
### 堆
### 树

![前端知识脑图](./assets/mindmap.png)