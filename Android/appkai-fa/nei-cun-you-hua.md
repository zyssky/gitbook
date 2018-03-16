概述：
Android 一个应用的可使用内存上限是固定的，当应用设计不当导致可使用内存不足或者使用了过多的内存导致系统剩余内存不足，这些都是应该避免的。
[CSDN-内存优化](http://blog.csdn.net/carson_ho/article/details/79549417?utm_source=tuicool&utm_medium=referral)

- 内存限制查看
```
内存的分配有ActivityManager来实现，因此也从此处来查看。
1,activityManager.getMemoryClass()获取普通应用的可分配内存大小
2,当在manifest中application中设置了android:largeHeap="true",通过
activityManager.getLargeMemoryClass()获取可分配内存大小
3，通过cat /system/build.prop 查看系统设置的dalvik.vm.heapsize
```

- 查看应用内存使用情况
```
//$package_name：应用包名
//$pid：应用进程ID，可以用PS命令查看
adb shell dumpsys meminfo $package_name or $pid 
结果分析后续给出
```

- 查看系统内存使用情况
```
由于所有应用的内存都是通过ActivityManager来分配的，因此也在这里查看系统内存情况，通过activityManager.getMemoryInfo()来查看。
```

- 内存泄漏（Memory Leak）
```
1,集合类，当对象从集合中拿出后，未及时将对应位置设为null
2，static 关键字修饰的成员变量,其生命周期相当于应用生命周期
3，非静态内部类 / 匿名类（此处统称为该类），默认持有外部类的引用，当该类未被销毁而其外部类需要被销毁时，外部类无法被销毁。
例子：
    3.1 在activity中使用多线程时，常因为要调用外部类而导致声明类非静态内部类，可以在activity结束时强制停止线程，或优化设计将线程类作为静态类
    3.2 Message中持有handler，Handler常以activity中匿名内部类形式定义，messagequeue持有message，当message没有在activity结束前处理，就会发生内存泄漏
4,资源对象使用后未关闭,对于资源的使用（如 广播BraodcastReceiver、文件流File、数据库游标Cursor、图片资源Bitmap等），若在Activity销毁时无及时关闭 / 注销这些资源，则这些资源将不会被回收，从而造成内存泄漏
5,动画未停止，在activity结束后，会被view持有引用
6，不良代码，构造 Adapter 时，没有使用缓存的 convertView ,每次都在创建新的 converView
```

- 内存泄漏解决方案
```
1，在不在使用集合中对象时，将集合中原对象位置设为null
2，在使用activity或者Context时，使用applicationContext
3，对于Handler泄漏，将Handler声明为静态内部类，将activity传入，用WeakReference包裹，OK！
4，在activity的onDestroy时关闭资源
5，对于动画（属性动画）将动画设置成无限循环播放repeatCount = “infinite”后，在Activity退出时记得停止动画
6，使用convertView，或者ViewHolder，就像使用recyclerview而不是listview
```
PS : [Handler泄漏以及避免详情](https://www.androiddesignpatterns.com/2013/01/inner-class-handler-memory-leak.html "Handler泄漏以及避免")

- 内存抖动
```
由于在短时间内大量的创建对象，然后不断触发gc，导致内存不稳定的现象，一般在循环中创建对象会造成该现象。
```

- bitmap处理
[CSDN-介绍](http://blog.csdn.net/carson_ho/article/details/79549382)
一般就用Glide

- 内存检查工具
```
1,LeakCanary 检测 Android 的内存泄漏，后续介绍
2,Android Studio 的Monitor监测内存使用情况，后续介绍
```

- 缓存和防止内存泄漏
```
SoftReference(软引用)用来做缓存，只有内存不足时的gc才会回收
WeakReference(弱引用)用来防止内存泄漏，一旦gc就会回收
```

- 代码和数据结构上的优化
![](/assets/内存优化-代码和数据结构.png)

内存泄漏总结：
![](/assets/内存泄漏情况统计.png)
