# SystemService
> 在开发过程当中，会需要用到的由手机管理的一些服务，包括各种常见的电话，键盘，指纹，定位，电池，等等，还有很密切关联的activitymanager，packagemanager，layoutinflator，windowmanager等等，都是由Context获取到，通过getSystemService来获取，然后应用本身利用相关调用

# Context
> 在中文中叫做上下文，也成为环境，那么到底能用来干嘛，该用来干嘛？其实，他就是用来获取一个Android应用该有的服务和资源的一个桥梁。我们用他来获取systemservice，assets，resources，theme，各种dir，classloader，四大组件的调用，权限等等与Android密切相关的操作，都会通过Context来进行

# activity

# service

# broadcast

# contentProvider & contentResolver

# fragment

# view （layout , 控件 , actionbar , 菜单，绘图）

# intent

# handler

# animation

# assets & resources

# notification

# toast

# sharedpreferneces

# sqlite3