> 这里不做Python语法和用法的详细介绍，只做我在已有基础上的一些补充和新的体会和感悟

## 杂七杂八
- \用来续行，但在(),{},[]中无需用\即可续行
- 冒号：用来表示包含，也就是增加一个缩进
- \#表示注释
- print默认换行，可用print("test",end="")来表示不换行
- 导入方式：1，import 2，from...import...
- 获取命令行参数，先导入sys，然后读取sys.argv
- 在交互模式中，最后被输出的表达式结果被赋值给变量 _
- 比较函数用 (x>y)-(x&lty) 取代


## 数据类型，结构，运算
- 无需声明，在被赋值后才被创建（如：count = 1 OK的！）
- 允许你同时为多个变量赋值（a=b=c=1）
- 一个变量可以通过赋值指向不同类型的对象
- 类型没有long，double，多了complex（a + bj,或者complex(a,b)表示），tuple和dictionary
- 类型识别用type(var)或isinstance(var,class)。type()不会认为子类是一种父类类型。isinstance()会认为子类是一种父类类型。
- True，False，可以与整数运算
- del语句删除一些对象引用，如：del var_a, var_b
-  2 / 4  # 除法，得到一个浮点数0.5<br/>
   2 // 4 # 除法，得到一个整数0<br/>
   2 ** 5 # 乘方得32
- 字符串截取：变量[头下标:尾下标]，尾下标不算入
- 原始字符（无转义），字符串前加r
- 字符串从右往左以-1开始，倒数第一个字符的意思
- 列表操作同字符串，只是其中的类型可以不同
- 元组（tuple）不可变，用()包起来使用，如：(1,2,3)
- tup1 = ()    # 空元组<br/>
tup2 = (20,) # 一个元素，需要在元素后添加逗号
- 集合使用大括号 { } 或者 set() 函数创建集合。创建一个空集合必须用 set() 而不是 { }，因为 { } 是用来创建一个空字典。
- 集合运算符，- 差，| 并，& 交，^ 异或
- 逻辑运算符为：and，or，not
- 身份运算符：is
- 关于not，为is not，not in
- round（），遵循结果为奇数弃，偶数进，当然只针对小数为0.5的时候。如：round(10.5) = 10！！！



## 流程控制
- else语句可以和for，while配合，如果 else 语句和 for 循环语句一起使用，else 语句块只在 for 循环正常终止时执行，而与while配合，当条件为False执行else
- 计数可用range()函数
- 有pass语句  

 
## 迭代器和生成器
- it = iter(),如：iter([1,2,3])
- next(it)
- 迭代器对象可以使用常规for语句进行遍历
- 使用了 yield 的函数被称为生成器（generator）。遇到 yield 时函数会暂停并保存当前所有的运行信息，返回yield的值。并在下一次执行 next()方法时从当前位置继续运行。<br/>我的理解就是写一个带有循环的函数，然后在半路yield一个值，即为迭代器调用next的值了。


## 函数
- 格式：<br/>
def 函数名（参数列表）:<br/>
- 参数：普通参数，默认值参数，关键字参数，可变参数，可变参数用*argv表示（使用，for arg in agrv,argv命名可变）
- lambda 函数：只一个语句。<br/>
语法：lambda [arg1 [,arg2,.....argn]]:expression
- 作用域：使用全局变量 要先声明一下：global arg，使用非全局但属于外部的变量，则：nonlocal arg
- 同时遍历几个列表，用zip()
- sorted(),reversed()返回对应操作后的序列
- enumerate() 可以用来产生带index的迭代

## 模块
- 内置的函数 dir() 可以找到模块内定义的所有名称。以一个字符串列表的形式返回
- 目录只有包含一个叫做 __init__.py 的文件才会被认作是一个包
- 如果包定义文件 __init__.py 存在一个叫做 __all__ 的列表变量，那么在使用 from package import * 的时候就把这个列表中的所有名字作为包内容导入。

## 输入和输出
- pickle模块实现了基本的数据序列和反序列化，<br/>
pickle.dump(obj, file, [,protocol])<br/>
x = pickle.load(file)

## 异常
- try:   except ZeroDivisionError as err:    finally：
- raise NameError("message")抛出异常
- 预定义清理行为with，如： with open("a.txt") as f:。。。。。。这样在完成后确保文件能关闭

## 面向对象
- class MyClass:
- 初始化：def \_\_init__(self,argv):
- 私有属性：用\_\_开头
- 继承：class MyClassA(MyClassB,MyClassC):
- 运算符重载，可以dir查看对应名称，然后重载



