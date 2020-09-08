[Toc]

在前端的面试中，`this` 指向与面向对象是必考题，也是日常开发中绕不开的话题，很多前端老鸟也会在 `this` 指向这里掉坑。本节围绕 `this` 指向问题，通过《`lol` 游戏》案例的编写，去分析 `this` 在不同环境下的不同指向



# 透彻认识 function 的 this 在不同调用环境下的指向

## 事件调用环境

谁触发事件，函数里的 `this` 指向的就是谁

## 全局环境

* 在浏览器环境下，全局的 `this` 指向的是 `window`
* 在 `node` 环境下，全局的 `this` 指向的是 `module.exports`

## 函数内部

* `this` 最终指向的是调用它的对象
  * 普通函数直接调用与 `window` 调用
  * 对象中的函数直接调用与 `window` 调用
* 函数被多层对象所包含，如果函数被最外层对象调用，`this` 指向的也只是它上一级的对象
  * 多层对象中的函数的 `this` 指向
  * 对象中的函数被赋值给另一个变量
* 构造函数中的 `this` 指向的是实例对象
  * 构造函数中的 `this` 指向
  * `new` 运算符的作用
* 如果构造函数中有 `return` ，如果 `return` 返回的指对象，`this` 指向返回的对象；如果不是对象，则 `this` 指向保持原来的规则，在这里，`null` 比较特殊

> new 运算符所做的事情：
>
> 1. 调用函数
> 2. 自动创建一个对象
> 3. 把创建出来的对象和 this 进行绑定
> 4. 如果构造函数没有返回值，隐式返回 this 对象

## 箭头函数中的 this 指向的特殊性

箭头函数本身是没有 `this` 和 `arguments` 的，在箭头函数中引用 `this` 实际上调用的是定义箭头函数的上一层作用域的 `this` 。这里强调一下是上一层作用域，因为对象是不能形成独立的作用域的

## 修改 this 指向

* 箭头函数中的 `this` 不能被修改
* 普通函数中的 `this` 可以使用 `call()` 函数修改
  * `call()` 函数中的第一个参数是要把 `this` 修改到那个对象上
  * 如果原函数还有参数，跟在 `call()` 函数的第一个参数后面即可

# 基于防抖和节流的性能优化

当下网页中的交互越来越多，很多高频事件带来的性能问题，已经是绕不过去的一个坎。怎么去优化这些高频事件呢？防抖和节流就必不可少。本节课从实际出发，详细讲解防抖与节流的使用。

## 手写防抖函数与字节流函数

### 防抖

就是指触发事件后在 `n` 秒内函数只能执行一次。如果在 `n` 秒内又出发了事件，则会重新计算函数执行时间

### 节流

就是指连续触发事件但是在一段时间中只执行一次函数

### css 重绘



### css 回流



## 掌握基于防抖与节流的性能优化





![image-20200625102720453](/Users/wchya/own/markdown/imgs/image-20200625102720453.png)