- 文件系统目录分别情况概述 -->[Android 4.2.2文件系统目录分析](http://blog.csdn.net/jscese/article/details/40897703)<br/>
```
/cache 
缓存目录
/data 
存放数据
/data/app 
目录下存放的就是用户安装的apk
/data/data 
目录下存放的是系统中所有app的数据文件，以apk包名区分,其中会有提交的数据库以及xml数据文件.
/dev linux
设备文件夹，存放设备节点文件，挂载的是tmpfs格式文件系统
/etc 
软连接指向/system/etc，这个目录一般用于存放系统中的各种配置文件
/mnt
外部挂载点目录，作为外部存储设备的挂载点路径，往下的分支常用的包括/mnt/sdcard为android默认SD卡挂载点.
/proc
一个虚拟的文件系统，由kernel提供，不是实际的存储空间，存在kenel管理的内存中，应用层可通过/proc下的文件动态获取kernel中系统进程(process)的运行信息.也可通过/proc/sys目录下可写文件修改kernel运行状态，实现与kernel的交互.
/sdcard
软连接上面说到的/mnt/sdcard，SD卡的挂载点
/sys
类似/proc，也是虚拟的文件系统.
区别在于这个文件系统提供的是关乎kernel中的设备驱动.
/system
这个是android系统最重要的文件目录了，可以在rc中看到挂载的是system分区，也就是源码编译出来的system.img镜像，主要的运行机制也就全在这个目录下了，默认是挂载成ext4只读.
1,/system/app系统预置的apk存放路径，只有root才有写权限
2,/sysem/bin这个下面全部是android系统可执行文件
3,/system/build.prop编译过程中收集的各种属性
4,/system/etc上面有提到，配置文件
5,/system/fonts字库
6,/system/framework下面全是jar包也就是源码中frameworks编译出来的系统框架，核心所在
7,/system/lib存放几乎所有编译出来的动态库(.so)
8,/system/vendor存放一些厂商的东西一般有applib之类的
这几个应该算是最重要的，其它的目录不一一列出.
如果想要修改/system下面的内容，可在shell终端输入：mount-o remount rw /system
重挂载为可读写.
```

- Android启动过程 --> [ Android——启动过程详解](http://blog.csdn.net/jscese/article/details/17115395)