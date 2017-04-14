---
title: Swift3.1新增的特性
date: 2017-04-13 23:03:25
tags: Swift学习
categories: iOS之路
---

> Apple最近发布了Xcode8.3, 以及Swift的一个小版本3.1。 不过不要担心, Swift3.1和Swift3是兼容的,这不会给你的Swift3项目造成太多的麻烦。不幸的是, Xcode8.3无情的去掉了对Swift2.3的支持, 所以, 如果你的项目在使用3.0之前的版本，个人建议还是不要着急更新。


## 数值类型的failable initialize

这个改动, 来自于[SE-0080](https://github.com/apple/swift-evolution/blob/master/proposals/0080-failable-numeric-initializers.md)。Swift为所有的数字类型定义了`failable initializer`, 当构造失败的时候, 就会返回`nil`。

```
Add a new family of numeric conversion initializers with the following signatures to all numeric types:
//  Conversions from all integer types.
init?(exactly value: Int8)
init?(exactly value: Int16)
init?(exactly value: Int32)
init?(exactly value: Int64)
init?(exactly value: Int)
init?(exactly value: UInt8)
init?(exactly value: UInt16)
init?(exactly value: UInt32)
init?(exactly value: UInt64)
init?(exactly value: UInt)

//  Conversions from all floating-point types.
init?(exactly value: Float)
init?(exactly value: Double)
#if arch(i386) || arch(x86_64)
init?(exactly value: Float80)
#endif
```

OK, 再让我们更直观的感受一下这个方法:

```
/// 行尾注释为运行结果
let a = 1.11
let b = Int(a)          //!< 1
let c = Int(exactly: a) //!< nil

let d = 1.0
let e = Int(exactly: d) //!< 1
```
在上面这段代码中, 我们可以看到`1.11 -> Int(exactly:) -> c`的结果为`nil`, 而`1.0 -> Int() -> e`的结果却是成功的。其实不难发现, `Int(exactly:)`比`Int()`的精度检查更加严格, 不会允许精度丢失的情况。因此`Int(exactly:)`转化时,如果丢失精度, 会返回nil。





