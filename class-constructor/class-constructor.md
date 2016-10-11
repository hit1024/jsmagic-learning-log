# class-constructor 没有继承的类系统

## 课后笔记

### 总tu结cao时间

* 道理我都懂，上手就蒙圈。上节课学习 bind 的时候，就想到属性继承顺序了，这节课是边看边点头。然而碰到第一道题：实现 Class，我的内心是崩溃的……
* 首先不知道该怎么设计接口—— Class 后面能不能接参数，还好有测试用例——要接参数。
* Class 接收的参数是啥，再看测试用例，哦，是用来做构造函数的。构造函数里的 this 要指向 Class 里面的闭包。
* Class 里面的闭包要返回吗？还是看测试用例 =.=!!貌似是否有返回无影响，也就是说不需要返回。

### 求解答
1. 测试数据分别是 {} 和 {'0': 1, '1': 2} 所以可以取巧定义只接收两个参数的函数。
        
{% gist 52d396098b9bf78aec24f0ea9f895af3 jsmagic-demo_code-part1.js %}

    假如要同时支持变长的参数，参数个数可以是两个、三个或者多个，该如何处理传参？比如：
        
        const constructor = function(a, b, c, d) {
            this.a = a;
            this.b = b;
            this.c = c;
            this.d = d;
        };


2. 第二个测试“Implement Instance Methods”里面第二项，“should not define `initialize` as a method”，为什么呢？
