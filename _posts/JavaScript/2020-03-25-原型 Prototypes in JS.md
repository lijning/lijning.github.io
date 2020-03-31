---
layout:     post
title:      "继承与原型链"
date:       2020-03-25 12:00:00
author:     "Jianing"
header-img: "img/post-bg-re-vs-ng2.jpg"
header-mask: 0.3
catalog:    true
tags:
  - JavaScript
---

# [继承与原型链](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)

## `__proto__` vs. `prototype`

[从`__proto__`和prototype来深入理解JS对象和原型链](https://github.com/creeperyang/blog/issues/9#)

- 对象的`__proto__`属性的值就是它所对应的原型对象
- 只有函数才有`prototype`属性 
  - 创建函数时，JS会为这个函数自动添加`prototype`属性，默认值是一个有 constructor 属性的对象，不是空对象。
  - 调用构造函数时创建的实例的`__proto__` 指向构造函数的`prototype`
-  `Function.prototype.__proto__`是标准的内置对象`Object.prototype` 

## 原型链

```js
Object.prototype.__proto__ === null;
```

- `Object.prototype`是原型链的顶端 

- `Object`/`Array`/`String`等等构造函数本质上和`Function`一样，均继承于`Function.prototype` ，后者直接继承顶端`Object.prototype` 。

## 性能

- 在原型链上查找属性比较耗时。
- 试图访问不存在的属性时会遍历整个原型链。
- 从 `Object.prototype` 继承的  `hasOwnProperty` 是 JavaScript 中一个处理属性并且**不会**遍历原型链的方法。 
-  在创建新的对象或者类时，方法通常应该关联于对象的原型，而不是定义到对象的构造器中。原因是这将导致每次构造器被调用时，方法都会被重新赋值一次（也就是，每个对象的创建）。 

```js
function MyObject(name, message) {
  this.name = name.toString();
  this.message = message.toString();
}
MyObject.prototype.getName = function() {
  return this.name;
};
```

