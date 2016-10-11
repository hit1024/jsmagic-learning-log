# what-is-this 什么是 this？

## 课后笔记

### bind 和 call 的效果是什么？

课程中提到，“this 代表函数运行时，自动生成的一个内部对象，只能在函数内部使用。”。

看完本节教程，理解 bind 的效果就是：接收一个类和该类的一个方法，返回一个特殊对象实例，这个对象实例在调用该方法时，方法里的 this 是指向对象实例的。

那么让我们实际在 node 中执行一下看看。

假设，一开始有一个对象 obj_origin，它有个方法 func，那么：

1. 首先是参数的初始化：

        $ node
        > const obj_origin = { name: "howard" };
        undefined
        > obj_origin.func = function(){console.log(`hello, my name is ${this.name}`);}
        [Function]

2. 当调用 `obj_origin.func()` 时，func 内部的 this 就是指向类的实体—— obj_origin。
3. 执行 `demo = obj_origin.func`，demo 是什么呢？node 中执行 `demo.toString()`

        $ node
        > demo = obj_origin.func
        [Function]
        > demo.toString()
        'function (){console.log(`hello, my name is ${this.name}`);}'
        > demo()
        hello, my name is undefined
        undefined
    
4. bind 是函数对象的一个方法，我们执行一下 `demo.bind(obj_origin)` 看看：

        $ node
        > obj_test = demo.bind(obj_origin)
        [Function: bound ]
        > obj_test.toString()
        'function () { [native code] }'
        > obj_test()
        hello, my name is howard
        undefined
        // 查了一下为什么会出现 [`function () { [native code] }`][1]，看完还是不懂，js 嘛，哈哈哈。bound 是啥？可能是个内建函数吧。
    
5. 来看看 call 吧：

        $ node
        > obj_origin.func.call(obj_origin)
        hello, my name is howard
        undefined
        > demo.call(obj_origin)
        hello, my name is howard
        undefined
        > obj_origin.func.call(obj_test)
        hello, my name is bound
        undefined
        // Hello, bound, nice to see you again, how do you do?




## 参考文献：
* [Function.prototype.bind()][0]
* [Function.prototype.toSource()][1]


[0]: https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Function/bind "Function.prototype.bind()"
[1]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/toSource "Function.prototype.toSource()"
