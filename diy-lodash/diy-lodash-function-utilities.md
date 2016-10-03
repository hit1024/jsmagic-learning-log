# diy-lodash-function-utilities 实现 Lodash 的工具函数


### 心得体会
* 握草，调用时才执行，还能缓存住结果，那不就是 Python 的 yield 么？哦，ES6 也有迭代器啦。
* 咦单线程，咦容易引起内存泄漏？嗯，还是有些适用的场景的，写成小的函数，并且少使用些变量呗。
* 一边测一边开发，有意思。


### 遇到不好理解的地方

* `git init -f`, 没有这个选项。
* 测试用例有三个，spec/bind_spce.js 这节课没用用上诶。
* mocha spec/memoize_spec.js。这个测试文件包含了两个测试用例：练习：缓存结果，练习：cache_key。在第一个练习那里，应该使用 `mocha spec  -g "should cache results"`，来执行第一个测试，否则会发现第二个测试失败，可能会令学员犯迷糊。


### 参考文献

* [ES6 Generators 工作原理](https://segmentfault.com/a/1190000006777434)
* [漫谈 JavaScript 函数](http://codethoughts.info/javascript/2015/06/22/javascript-functions/)
* [Checking if a key exists in a JavaScript object?](http://stackoverflow.com/questions/1098040/checking-if-a-key-exists-in-a-javascript-object/1098955#1098955)
