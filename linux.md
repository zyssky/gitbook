- 硬链接和软链接 [@网页链接](https://www.ibm.com/developerworks/cn/linux/l-cn-hardandsymb-links/index.html)
> 查找文件是通过:文件名-->inode-->data——block,这种方式，硬链接是多个文件名指向同一个iNode，而软链接实质是创建了一个文件，在data——block内容中指向了文件的路径名而已。

- 开启后台服务
> nohup cmd params &