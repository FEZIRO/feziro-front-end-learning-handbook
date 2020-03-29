# 前端学习对比手册(By FEZIRO)
#### 我很喜欢以对比的方式学习一些容易混淆或者迷惑的前端特性和概念
<br>

## 伪类和伪元素对比
 名称 | 语法 | 数量 | 作用
-|-|-|-
伪类 | ： | 可单个可多个叠加 | 基于DOM产生不同修饰DOM元素的状态
伪元素 | ：： | 只能单个使用 | 创建不存在DOM中的新元素对象
<br/>

## let和const和var对比
 名称 | 变量提升 | 全局变量 | 重复声明 | 重新赋值 | 暂时死区|块作用域|只声明不初始化
 -|-|-|-|-|-|-|-|
var|√|√|√|√|x|x|√
let |x|x|x|√|√|√|√
const|x|x|x|x|√|√|x
<br>

## visiable：hidden 和 opacity：0 和 display：none对比
名称|作用|可否点击
-|-|-|
visiable：hidden|占位隐藏|否
opacity：0|占位隐藏|是
display：none|不占位隐藏|否
<br>

## 单行溢出隐藏、多行溢出隐藏
名称| css
-|-
单行溢出|`width:150px(固定宽度)`<br>`white-space:no-wrap`<br>`overflow:hidden`<br>`text-overflow:ellipsis`
多行溢出|`width:150px（固定宽度）`<br>`display:-webkit-box;`<br>`-webkit-box-orient:vertical`<br>`-webkit-line-camp:3`<br>`overflow:hidden`
<br>

## Set、Map和WeakSet、WeakMap的区别
1. WeakSet和WeakMap类没有entiries, keys, values等方法，无法被遍历。
2. WeakSet和WeakMap类只能用对象作为键（key），没有强引用的键，垃圾回收机制可以回收。
3. set, map键和值可以是任意类型。
<br>

## flex：1是什么
flex：1|等于
-|-
flex：1|flex-grow：1;<br>flex-shrink: 1;<br>flex-basis: 1;<br>
<br>

## flex布局子项单独靠右
```
  //父元素
  display: flex;
  align-items: center;

  （方法1）
  //子元素
  flex: 1;
  text-align: right;

  （方法2）
  //子元素
  margin-left: auto;
```
<br>

## 垃圾回收GC机制
机制|工作原理
-|-
标记清除|标记方式：特殊位的反转、维护一个列表<br>原理：垃圾收集器在运行的时候会给存储在内存中的所有变量都加上标记，然后它会去掉环境中的变量已经被环境中变量被标记为引用的变量，在此之后再被标记的变量将被视为准备删除的变量。最后垃圾回收器清除标记的变量，回收它们所占用的内存空间，目前主流浏览器都是使用标记清除式的垃圾回收策略，只不过收集的间隔有所不同。
引用计数| 原理：每次引用加一，被释放时减一，当这个值的引用次数变成 0 时，就可以将其内存空间回收<br>缺点：循环引用(obj1 和 obj2 通过各自的属性相互引用，也就是说，这两个对象的引用次数都是 2)

<br>

## ES7/ES8新特性
版本|新特性
-|-
ES7| 求幂运算符（**）<br>新增Array.prototype.includes()方法<br>Object.getOwnPropertyDescriptors获取对象的属性描述符
ES8| async、await异步解决方案<br>Object.entries()<br>Object.values()<br>字符串填充padStart()、padEnd()



<br>

## OSI七层网络模型
![OSI模型图](https://github.com/FEZIRO/feziro-front-end-learning-handbook/blob/master/images/20190105161812494.png)

