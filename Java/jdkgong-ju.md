- jps
> 查看java进程的进程号的工具

- jmap
> 一个内存映射工具
> jmap -heap 进程号
> jmap -dump:file="filename.bin" 进程号 //得到当前堆dump

- jhat
> 分析dump堆信息。
> jhat dump.bin //一般就可以在localhost：7000查看了

- jstack
> 是一个生成指定 JVM 进程的线程堆栈工具.当你程序一直在那里转圈圈，而你想找到线程到底做了什么导致死锁，那么 jstack 最适合。
> jstack -F -l 进程号

- javap
> 反编译工具，但只能简单查看方法和Field而已
> javap *.class
> javap -p *.class //查看非public方法和Fields

- jar
> 管理和创建jar，war，ear的工具
> jar cvf Build.jar * //把当前目录的class和子目录的class打包成Build.jar
> jar tvf Builded.jar //查看jar文件内部东西
> jar xvf Builded.jar //提取jar文件内部所以东西
> jar uvf Builded.jar newfile.txt //将newfile.txt加入jar中
> 说明：c 创建，t 查看，x 提取，u 更新，v verbose，f 指定文件名。当然很多操作都可以在压缩工具中完成。在idea中可以配置project structure来生成artifacts