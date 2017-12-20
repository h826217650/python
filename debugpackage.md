## 1 debug包与release包的区别
[Xcode Debug、Release、Archive、Profile、Analyze概念解释](http://blog.csdn.net/mad1989/article/details/40658033)  

- Debug是调试版本，包括的程序信息更多
- 只有Debug版的程序才能设置断点、单步执行、使用TRACE/ASSERT等调试输出语句
- Release不包含任何调试信息，所以体积小、运行速度快

## 2 如何打包
Xcode左上角，点中项目名称-Edit Scheme，或是菜单栏-Product-Scheme-Edit Scheme 弹出界面如下：

![](/Users/huxiaoyan/Desktop/debug与release.jpeg)

当你这里设置Debug时，你build/Run后就是debug版本，相应的，修改成Release模式，出来的就是release版本，这里可以很方便切换。


## 2 debug包如何去掉assert断言

- 全局搜 “KSAssertionHepler.h”
- 修改全局import  
![](/Users/huxiaoyan/Desktop/debugassert.png)

- 然后打包即可