Q1：	是否遇到过浏览器的兼容性问题？有没有什么令你印象深刻的兼容性问题？

A:
* safari 和 firefox/chrome 在 data object 上的实现不一致。具体表现为 new Date('date') 中的 date 的格式问题
* html 5 滚动穿透。产生原因/safari/方案/方案原理


Q2:	是否遇到过移动端面的兼容性问题？有没有什么令你印象深刻的兼容性问题？

* 滚动条/拖拽。需要更多具体细节
* 比如 iPad 下，横竖屏切换时，要保证 UI 显示正确的尺寸。window.addEventListener('orientationchange', callback)


Q3:	跨域有哪几种方式？你知道几种？

1. jsonp。限制：只能适用于 get 方法
2. 后台设置 CORS Access-Control-Allow-Origin。但 Access-Control-Allow-Origin，只能使用 \*/完整的 url。因此如果需要针对特定的 url 采用特定的跨预策略，可以使用 request header 里的 referer 获取到访问源的 url，并依此来判断
3. postMessage
4. iframe 作代理(3 种)，利用 src tag 的跨域能力。如使用 hash、使用 window.name、
5. 利用 nginx 作反向代理


Q4:	不同子域之间，如果设置 domain.name = '主域'，那么子域时间是否是同域？


Q5:	你知道洋葱圈模型吗？


Q6:	正则表达式


Q7:	cookie


Q8:	AOP


Q9:	安全问题 XSS/CSRF
* xss，跨站脚本攻击，通过在 url 中插入特殊字符串，如 script 标签等，注入恶意脚本。解决方案是
1. encode 特殊字符，如 <>&，再做 decode 整个 url
2. 如果是富文本，可以使用白名单的方式。什么是白名单？就是指只允许特定的标签，或其他内容，按照特定的格式呈现，超出该限制一律禁止。
* csrf 跨站请求伪造


Q10:	事件捕获/事件冒泡 不同点，哪些事件不能事件捕获


Q11:	性能问题：雅虎性能优化34条


Q12:	闭包  什么是闭包？早期的闭包一般有什么应用？
* 闭包是一个可以读取其他函数中变量的函数。而在 javascript 中，只有函数的子函数才可以读取外部的局部变量，因此可以简单理解成函数内部的函数。
* 用途：读取函数内部的变量
* 用途：让变量一直保持在内存中。可以把变量像属性一样存在闭包里，后面可以一直使用它。
* http://blog.csdn.net/qq_34986769/article/details/52171174


Q13:	原型链


Q14:	react 和传统 jQuery 等前端开发方式 有什么区别，优势劣势在哪里？virtual dom 的优势在哪里？


Q15：	jQuery 上有完整的生态，如果 React 上没有相应的库，有没有自己根据业务需求做过 React 组件库？


Q16：	你用过node/mongodb，但是 mongodb 没有 mySQL 那样的锁机制，如果用多个用户对数据做操作，你是怎么解决 mongodb 类似的锁的问题的


Q17：	parent.prototype.a, child.prototype.a，请问 this.a 的内存寻址过程


Q18：	输入 url 以后，具体都发生了些什么？如资源如何加载等等


Q19：	webpack 和 browserify 你都用过，有什么区别？webpack 的机制是什么，有什么优势？browserify 的机制是什么，底层实现？


Q20：	webpack 编译文件时，如果文件过多，如何优化？编译上要做些什么处理？如何减少最终打包文件的体积？


Q21：	ios html 的滚动穿透问题是因何引起的？相关解决方案/库的底层方案原理有没有了解过？


Q22：	flux 是什么？有什么特点？核心思想/概念 等等


Q23:  你知道正则引擎吗？DFA、NFA/POSIX_NFA 的区别？
* Javascript 用的是 Traditional NFA，即传统的 NFA。
* 贪婪模式，或者叫忽略优先量词。形如 {}?、\*?、??、+?
* 前向查找，或者叫正向环视。形如 (?=exp)、(?!exp)
* 零宽表达式。匹配后返回的是位置，不占用字符，或者匹配结果**不保存**在最终结果里面的，叫零宽表达式
* 控制权与传动。控制权的传动指的是正则表达式每个表达式的传动


Q24:  AMD 规范/CMD 规范



Q25： undefined vs null


Q26:  如何监听 history.pushState ？

h5 没有提供官方接口来监听 history.pushState。但可以 hack 实现
```
function (history) {
  var pushState = history.pushState
  history.pushState = function (state) {
    if (typeof history.onpushstate === 'function') {
      history.onpushstate({state: state})
    }

    // ... whatever else you want to do
    // maybe call onhashchange e.handler
    return pushState.apply(history, arguments)
  }
}(window.history)
```


Q26-1:	window.onhashchange 是什么？如何工作？它和监听 history.pushState 的方法有什么区别？onpopstate 呢？

* onhashchange 是监听 url 的 hash 值是否变化，具体来说，如果 url 只有 # 后面的锚点发生了变化，也就是 hash 变化了，会触发 hashchange。注意，pushState 绝不会触发 hashchange，即使 pushState 的 url 只修改了 hash 值。
* pushState 的 hack 监听方法会监听所有的 pushState 的指令，但 onhashchange 只会监听 hashchange，pushState 导致 hash 变化不会监听到
* onpopstate 在浏览器 a) 前进/后退 b) history.go/back/forward 调用 c) hashchange/锚点改变 时都会触发。pushState 导致的 hashchange 不会触发 popstate
* pushState 需要有一个参数，第一个参数是 stateObj，会修改 history 的 state 对象；第二个参数是 title，目前没用；第三参数是 url 的路径，相对路径、绝对路径都行，相对路径会把 url path 及之后的部分整体替换掉，绝对路径是整体替换，但要注意，无论是绝对路径，还是相对路径，必须和当前 url 是同源的  


如果管理 history 的变化？


Q27：react 的 DOM tree 是怎么样的？什么是虚拟 DOM tree？react 的两棵 DOM tree


Q28: for-in 是什么？for-in 用在数组上什么效果？for-of 是什么？数组/对象上分别是什么效果？
* for-in 遍历一个对象的所有**可枚举属性**。应用在对象上，每次迭代的元素是对象的键(key)
* for-in 用在数组上，如 for (let ele in array)，迭代的每个元素 ele 是 array 的索引，或者叫下标。因为数组本身就是一个对象，所以它的每个索引可以看作一个是可枚举属性，具体来说就是对象中的某个 key。严格来说 for-in 不应该应用在数组上，因为顺序在数组中很重要，数组本质上是可枚举属性是整数的对象，而把 for-in 应用在数组上，不能够保证顺序与预期一致，因为 for-in 每次迭代中可枚举属性的值是依赖上下文的。若需要迭代数组，应该使用 for 的整数引用做循环，或者使用 Array 的 forEach 方法
* for-of 在可迭代对象上创建一个迭代循环，每次迭代中的元素是属性对应的值，而不是属性本身
* for-of 应用在对象上，要看对象本身是否是可迭代的，因为 for-of 只能应用在可迭代对象上


Q29：什么是可枚举属性？



Q30-1: url 字符编码要注意什么?  
A: 为了防止 xss，有些字符需要做 encode  
Q30-2: 哪些字符需要 encode ?  
A: 比较典型的像 <、>、& 这些，它们能向页面插入 script tag，从而使黑客获得插入脚本的能力。  
Q30-3: 黑客怎样通过 xss 进行攻击？  
A: 比如说插入一个 script tag、或者是 img tag，利用标签 src 本身的跨域能力，就可以加载黑客服务器上的入侵脚本。脚本可以监听登录框的用户密码输入，或是埋钓鱼链接、在一些跳转链接后面隐藏其他 iframe、img 之类的
Q30-4: 哪些字符不能被 encode ? 或者问 encodeURI 和 encodeURIComponent 的区别  
A: 包含三个部分。第一部分是大小写字母，数字，不能被 encode；第二部分是不属于 url 的特殊字符，比如 ()\_\. 等等；第三部分是 url 里的特殊字符，比如 / : ? = & # @ 等等。第三部分的字符可以被 encodeURIComponent encode，但是不能被 encodeURI encode，其他两块的字符都不能被这两个方法 encode


Q31: flexbox 详解/盒模型详解  
https://css-tricks.com/snippets/css/a-guide-to-flexbox/  
https://css-tricks.com/flex-grow-is-weird/  
https://stackoverflow.com/questions/41033245/does-position-absolute-conflict-with-flexbox  

Q32: js 如何遍历一棵树？树可以有哪些方法？用 js 实现一下


Q33：如何实现深拷贝？或者说，怎么实现 Object.assign 的功能

Q34: Object.create 和 new 有什么区别

Q35: delete 和 null 删除值的时候有什么区别

Q36: 箭头函数和 es5 的 function 有什么区别？

最后你有什么问题想问我的吗？
如果技术题都能答上，那么可以问问公司发展或者技术/人员构成之类的问题，如：
* 贵公司的组织架构大概是什么样的？
* 贵公司前端一般用些什么样的技术？
如果技术题能答，但不全面，或者很多问题自己明显感觉答的有问题，那么可以问一些技巧性的问题，如：
* 您觉得我目前技术上哪里需要提高，怎么提高？
* 你们前端这块最近在寻找什么样的候选人？需要满足些什么条件？
或者和我目前情况相近，技术上比较欠缺，基础知识不扎实，技术面明显成问题的，可以问些如何成长之类的问题，如：
* 您觉得怎样可以真理深入理解原理，快速提升？分析代码，然后自己造轮子是一种比较好的方式吗？

Q37: 严格模式下和非严格模式下，this 有什么区别？
* 严格模式下，传给 this 的值不会被自动强制转化成对象，如：
```
'use strict'
function foo() { return this; }
foo() === undefined 		// true, 非严格模式下，foo() === 全局对象，浏览器环境下是 Window
foo.call(2) === 2   		// true, 非严格模式下，foo.call(2) 应为对象，typeof foo.call(2) === 'object'
foo.call(null) === null		// true, 非严格模式下，foo.call(null) 应为 Window 对象
foo.call(undefined) === undefined // true, 非严格模式，同 null 的情形
foo.call('str') === 'str'	// true, 非严格模式下，foo.call('str') 应为对象，typeof foo.call('str') === 'object'
foo.call(false) === false	// true, 非严格模式下，同 str/number
```

Q38: 箭头函数和 es5 的 function 函数有什么区别？
* 箭头函数没有自己的 this, arguments, 没有 new 操作符，没有 prototype 属性
* 箭头函数没有 generator 用法, 也就是没有 yield
* 如果是箭头函数，严格模式中与 this 相关的规则会被忽略，如
```
'use strict'
var fArrow = () => {
  console.log(this === window);	// true
}
fArrow()
---------------------------------------
'use strict'
var fNormal = function() {
  console.log(this === undefined);	// true
}
fNormal()
```
那箭头函数的 this 来自哪里？下面代码的输出结果是什么？  
* 箭头函数的 this 使用的是**执行上下文**的 this。举个例子：
```
function foo() {
  this.cnt = 0;
  setInterval(() => {
    this.cnt++
    // 这里的 this 和上面的 foo 的 this 是同一个，若是 function 的话，这里的 this 就是全局对象 Window 了
    console.log(this)	
  }, 1000)
}
var f = new foo()
```

### code understanding
Q1:
```
var name = "The Window";

var object = {
　　name : "My Object",
　　getNameFunc : function(){
　　　　return function(){
　　　　　　return this.name;
　　　　};
　　}
};

alert(object.getNameFunc()());
```
这段代码输出什么结果？


Q2:
```
var name = "The Window";

var object = {
　　name : "My Object",
　　getNameFunc : function(){
　　　　var that = this;
　　　　return function(){
　　　　　　return that.name;
　　　　};
　　}
};

alert(object.getNameFunc()());
```
这段代码输出什么结果？


Q3:
```
const arr = [4, 'str', '029', 2039, { key: 'val' }]
for (let ele in arr) {
	console.log(ele)
}
```
这段代码输出什么？




0322_众安保险面试补充
非受控的 select 组件是如何管理 state 的？
doctype 是什么？有什么用？


react/性能/安全/兼容性
