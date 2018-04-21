# 面试准备

## 基础问题

1. `UIView` 和 `CALayer` 是什么关系？

   官方文档对 `UIView` 的 `layer` 属性注释是：**returns view's layer. Will always return a non-nil value. view is layer's delegate**。

   由此可见 `UIView` 和 `CALayer` 的主要关系是：`UIView` 是 `CALayer` 的 delegate。

   除此之外：每个 `UIView` 都有一个 `CALayer`，`UIView` 可以响应触摸事件，而 `CALayer `不可以，`UIView` 主要侧重对显示内容的管理，而`CALayer` 主要侧重对显示内容的绘制。

2. `Bounds` 和 `Frame` 的区别？

   `Bounds`：该 view 在本地坐标系统中的位置和大小。

   `Frame`：该 view 在父 view 坐标系统中的位置和大小。

   `Bounds` 和`Frame` 的 width、height 并不一定相等，在当 view 做 旋转 transform 时，就不相等。

3. 如何高性能的画一个圆角？

   `UIView`：使用 `Core Graphics` 画出一个圆角 image，然后把 image 添加到 view 的最底层。

   `UIImageView`：使用 `Core Graphics` 直接截取 UIImageView 的 image。

   [参考资料](https://bestswifter.com/efficient-rounded-corner/)

4. `load`  和 `Initialize` 的区别？

   ① `load` 在这个文件被程序装载时调用，`initialize` 在第一次给某个类发送消息时调用。前者在 main 函数之前调用，后者在之后调用。

   ② `load `和 `initialize` 方法都不用显示的调用父类的方法而是自动调用，即使子类没有 `initialize` 方法也会调用父类的方法，而 `load` 方法则不会调用父类。

   ③ `load` 方法通常用来进行 Method Swizzle，`initialize` 方法一般用于初始化全局变量或静态变量。

   ④ `load` 和 `initialize` 方法内部使用了锁，因此它们是线程安全的。实现时要尽可能保持简单，避免阻塞线程，不要再使用锁。

   [参考资料](https://bestswifter.com/load-and-initialize/#initialize)

5. `Designated Initializer` 的规则？

   ① 便利初始化函数只能调用自己类中的其他初始化方法

   ② 指定初始化函数才有资格调用父类的指定初始化函数

   ![](https://github.com/yyny1789/InterviewPreparation/blob/master/pics/designated.png?raw=true)

## 经验问题

## 哲学问题

## 算法

## 参考

1. [iOS 开发者面试题集锦](https://github.com/liberalisman/iOS-InterviewQuestion-collection)

