# 面试准备

## 基础问题

1. `UIView` 和 `CALayer` 是什么关系？

   ```swift
   @property(nonatomic,readonly,strong) CALayer  *layer; // returns view's layer. Will always return a non-nil value. view is layer's delegate
   ```

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

   ① 便利初始化函数只能调用自己类中的其他初始化方法。

   ② 指定初始化函数才有资格调用父类的指定初始化函数。

   <img src="https://github.com/yyny1789/InterviewPreparation/blob/master/pics/designated.png?raw=true" width="500" />

6. `LoadView` 方法的作用？

   ```swift
   - (void)loadView; // This is where subclasses should create their custom view hierarchy if they aren't using a nib. Should never be called directly.
   ```

   用来自定义一个 view 给 viewController 使用。

7. 说一下控制器 `View` 的生命周期，一旦收到内存警告该如何处理？

   生命周期： `init -> loadView -> viewDidLoad -> viewWillAppear -> viewDidAppear -> viewWillDisappear -> viewDidDisappear -> dealloc `

   内存警告：当 App 收到内存警告时，会调用 `view controller` 的 `didReceiveMemoryWarning` 方法，所以在 `didReceiveMemoryWarning` 里做一些减少内存的操作。

   ```swift
   override func didReceiveMemoryWarning() {
          	super.didReceiveMemoryWarning()
           
           if self.isViewLoaded && self.view.window == nil {
               self.view = nil
           }
           self.dataArr.removeAll()
       }
   ```

8. 简述事件传递、事件响应机制。

   南峰子的这篇 [UIKit: UIResponder](http://southpeak.github.io/2015/03/07/cocoa-uikit-uiresponder/) 文章介绍的很详细。

9. 怎样扩大 `UIButton` 点击范围？

   [UIButton: Making the hit area larger than the default hit area](https://stackoverflow.com/questions/808503/uibutton-making-the-hit-area-larger-than-the-default-hit-area) 

   需要理解 UIKit：UIResponder。

10. `setNeedsLayout` 和 `layoutIfNeeded` 的关系？

   ```swift
   // Allows you to perform layout before the drawing cycle happens. -layoutIfNeeded forces layout early
   - (void)setNeedsLayout;
   - (void)layoutIfNeeded;
   ```

   `setNeedsLayout` ：标记为需要重新布局，不立即刷新，在下一轮 `runloop` 结束前刷新。

   `layoutIfNeeded` ：如果有需要刷新的标记，立即调用 `layoutSubviews` 进行布局。

   这两个方法一般是配套使用，也可单独使用。

11. `RunLoop` 是什么？

    [深入理解RunLoop](https://blog.ibireme.com/2015/05/18/runloop/)

    [iOS线下分享《RunLoop》by 孙源@sunnyxx](http://v.youku.com/v_show/id_XODgxODkzODI0.html)

## 经验问题

## 哲学问题

## 算法

## 参考

1. [iOS 开发者面试题集锦](https://github.com/liberalisman/iOS-InterviewQuestion-collection)

