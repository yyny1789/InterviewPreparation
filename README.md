# 面试准备

## 基础问题

1. `UIView` 和 `CALayer` 是什么关系？

   官方文档对 `UIView` 的 `layer` 属性注释是：**returns view's layer. Will always return a non-nil value. view is layer's delegate**。

   由此可见 `UIView` 和 `CALayer` 的主要关系是：`UIView` 是 `CALayer` 的 delegate。

   除此之外：每个 `UIView` 都有一个 `CALayer`，`UIView` 可以响应触摸事件，而 `CALayer `不可以，`UIView` 主要侧重对显示内容的管理，而`CALayer` 主要侧重对显示内容的绘制。

2. `Bounds` 和 `Frame` 的区别?

   `Bounds`：该 view 在本地坐标系统中的位置和大小。

   `Frame`：该 view 在父 view 坐标系统中的位置和大小。

   `Bounds` 和`Frame` 的 width、height 并不一定相等，在当 view 做 transformed 时，就不相等。

3. 如何高性能的画一个圆角?

   `UIView`：使用 `Core Graphics` 画出一个圆角 image，然后把 image 添加到 view 的最底层。

   `UIImageView`：使用 `Core Graphics` 直接截取 UIImageView 的 image。

   [参考资料](https://bestswifter.com/efficient-rounded-corner/)

## 经验问题

## 哲学问题

## 算法

## 参考



