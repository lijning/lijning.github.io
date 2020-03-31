---
layout:     post
title:      "JavaScript基本数据类型"
date:       2020-03-25 12:00:00
author:     "Jianing"
header-img: "img/post-bg-re-vs-ng2.jpg"
header-mask: 0.3
catalog:    true
tags:
  - JavaScript
---

# Data Types in JavaScript

## JS: Basic datatypes

- Number, String, `Boolean`, `undefined`, `Null`, object
- `Bigint`, `Symbol` (new in ES6)
- 唯一的引用类型和可变类型： `object`。 此外均属于 primitive values
- 字符串：  一组16位的无符号整数值的“元素”  ; immutable
- Function： 一种特殊的object

### 基本包装类型

- Boolean,  Number, String 
- 基本包装类型在代码执行后就会销毁实例，生存期和引用类型不同。 
  - :pear: `'str'.method()` 调用时创建包装对象，调用完毕立即销毁。
- 也可使用一个new来创建对象，使之成为持久的引用类型。 

[JS数据类型分类和判断](https://juejin.im/post/5b2b0a6051882574de4f3d96)

[MDN](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Data_structures)

[类型系统](https://www.zhihu.com/question/40683360) 《 JavaScript高级程序设计 》 

## Number

-  JS 中所有的数字类型，实际存储都是通过 8 字节 [double 浮点型](http://zh.wikipedia.org/wiki/雙精度浮點數) 表示的。 

[JS 的整型你懂了吗？](https://segmentfault.com/a/1190000002608050)