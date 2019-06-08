## python函数
函数数学定义  
&nbsp;&nbsp;&nbsp;&nbsp;y=f(x),y是x的函数，x是自变量。y=f(x0,x1,...,xn)  

python函数  
&nbsp;&nbsp;&nbsp;&nbsp;由若干语句组成的语句块、函数名称、参数列表构成，它是组织代码的最小单元  
&nbsp;&nbsp;&nbsp;&nbsp;可以完成一定的功能  

函数的作用  
&nbsp;&nbsp;&nbsp;&nbsp;结构化编程对代码的基本的封装，一般按照功能组织一段代码  
&nbsp;&nbsp;&nbsp;&nbsp;封装的目的为了复用，减少冗余代码  
&nbsp;&nbsp;&nbsp;&nbsp;代码更加简洁美观、可读易懂  

函数的分类  
&nbsp;&nbsp;&nbsp;&nbsp;内建函数，如max()、reversed()等  
&nbsp;&nbsp;&nbsp;&nbsp;库函数、如math.ceil()等  
&nbsp;&nbsp;&nbsp;&nbsp;自定义函数，使用def关键字定义  

##### 函数定义
>def 函数名(参数列表):  
&nbsp;&nbsp;&nbsp;&nbsp;函数名(代码块)  
&nbsp;&nbsp;&nbsp;&nbsp;[return 返回值]

* 函数名就是标识符，命名要求一样
* 语句块必须缩进，约定四个空格
* python的函数若没有return语句，就会隐式返回一个None值
* 定义中的参数列表称为**形式参数**，只是一种符合表达(标识符)，简称**形参**  

##### 函数调用
函数定义，只是声明了一个函数，他不能被执行，需要调用  
调用的方式，就是**函数名后加上小括号**，如果必要在括号内填写上参数  
调用时写的参数式**实际参数**，是实实在在传入的值，简称**实参**  

>def add(x,y): &nbsp;&nbsp;# 函数定义  
&nbsp;&nbsp;&nbsp;&nbsp;result = x + y  &nbsp;&nbsp;# 函数体  
&nbsp;&nbsp;&nbsp;&nbsp;return result&nbsp;&nbsp;&nbsp;&nbsp;# 返回值  
out = add(4,5) &nbsp;&nbsp;# 函数调用，可能有返回值，使用变量接受这个返回值  
print(out) &nbsp;&nbsp;# print函数加上括号也是调用  

上面代码解释：  
* 定义一个函数add，及函数名是add，接受2个参数
* 该函数计算的结果，通过返回值返回，需要return语句
* 调用时，通过函数名add后加上两个参数，返回值可使用变量接受。
* **函数名也是标识符，返回值也是值**
* 定义需要在调用前，也就是说调用时，已经被定义过了，否则抛出NameError异常
* 函数时**可调用的对象**，callable()

### 函数参数
函数在定义要约定好形式参数，调用时也提供足够的实际参数，一般来说，形参和实参个数要一致（可变参数除外）
##### 传参方式
1. 位置传参  
 定义时def f(x,y,z)，调用使用f(1,3,5),按照参数定义顺序传入参数
2. 关键字传参  
 定义时def f(x,y,z),调用使用f(x=1,y=3,z=5),使用形参的名字来传入实参的方式，如果使用了形参名字，那么传参顺序就可和定义顺序不同  

**要求位置参数必须在关键字参数之前传入**，位置参数是按位置对应的  
##### 参数缺省值
缺省值也称为默认值，可以在函数定义时，为形参增加一个缺省值。作用是：参数的默认值可以在未传入足够的实参的时候，对没有给定的参数赋值为默认值；参数非常多的时候，并不需要用户每次都输入所有的参数，简化函数调用

##### 可变参数
1. 可变位置参数  
 &nbsp;&nbsp;在形参前使用 * 表示该形参是可变位置参数，可以接受多个实参  
 &nbsp;&nbsp;它将收集来的实参组织到一个tuple中
2. 可变关键字参数  
 &nbsp;&nbsp;在形参前使用 ** 表示该形参是可变关键字参数，可以接受多个关键字参数  
 &nbsp;&nbsp;它将收集来的实参的名称和值，组织到dict中  

混合使用时，要有可变位置参数和可变关键字参数，普通参数需要放到参数列表前面，可变参数要放到参数列表的后面，可变位置参数需要在可变关键字参数之前

##### keyword-only参数
在形参定义时，在一个 * 星号之后，或一个可变位置参数之后，出现的普通参数，就已经不是普通的参数了，称为keyword-only参数。  

keyword-only参数，就是这个参数必须采用关键字传参，因为前面的可变关键字参数已经截获了所有位置参数，其后的变量x不可能通过位置传参传入了。  

##### 参数规则
参数列表参数一般顺序是：普通参数、缺省参数、可变位置参数、keyword-only参数（可带缺省值）、可变关键字参数。  
注意：  
&nbsp;&nbsp;&nbsp;&nbsp;代码应该是易读易懂，而不是为难别人  
&nbsp;&nbsp;&nbsp;&nbsp;请按照书写习惯定义函数参数  
&nbsp;&nbsp;&nbsp;&nbsp;定义最常用参数为普通参数，可不提供缺省值，必须由用户提供。注意这些参数的顺序，最常用的先定义  
&nbsp;&nbsp;&nbsp;&nbsp;将必须使用名称的才能使用的参数，定义为keyword-only参数，要求必须使用关键字传参  
&nbsp;&nbsp;&nbsp;&nbsp;如果函数有很多参数，无法逐一定义，可使用可变参数，如果需要知道这些参数的意义，则使用可变关键字参数收集  

##### 参数解构
* 在给函数提供实参的时候，可以在可迭代对象前使用 * 或者 ** 来进行结构的解构，提取出其中所有元素作为函数的实参
* 使用 * 解构成位置传参
* 使用 ** 解构成关键字传参
* 提取出来的元素数目要和参数的要求匹配

***
#### 函数返回值
* python函数使用return语句返回"返回值"
* 所有函数都有返回值，如果没有return语句，隐式调用return None
* return语句并不一定是函数的语句块的最后一条语句
* 一个函数可以存在多个return语句，但是只有一条可以被执行。如果没有一条return语句被执行到，隐式调用return None
* 如果有必要，可以显示调用return None，可以简写为return
* 如果函数执行了return语句，函数就会返回，当前被执行的return语句之后的其他语句就不会被执行了
* 返回值的作用：结束函数调用、返回"返回值"
* 函数必能同时返回多个值
* return 1, 3, 5 看似返回多个值，隐式的被python封装成了一个元组

### 函数作用域
作用域  
&nbsp;&nbsp;&nbsp;&nbsp;一个标识符的可见范围，这就是标识符的作用域。一般常说的是变量的作用域。函数是一个封装，它会开辟一个作用域，函数里的变量会被限制在这个作用域中，所以函数内部的变量在外部不可见。  
&nbsp;&nbsp;&nbsp;&nbsp;每一个函数都会开辟一个作用域  

##### 作用域分类
全局作用域  
&nbsp;&nbsp;&nbsp;&nbsp;在整个程序运行环境中都可见  
&nbsp;&nbsp;&nbsp;&nbsp;全局作用域中的变量称为全局变量  

局部变量  
&nbsp;&nbsp;&nbsp;&nbsp;在函数、类等内部可见  
&nbsp;&nbsp;&nbsp;&nbsp;局部作用域中的变量称为局部变量，其使用范围不能超过所在局部作用域  

一般来讲外部作用域变量在函数内部可见，可以引用  
反过来，函数内部的局部变量，不能在函数外部看到  

#### 函数嵌套
在一个函数中定义了另一个函数
>def outer():  
&nbsp;&nbsp;&nbsp;&nbsp;def inner():  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;print("inner")  
&nbsp;&nbsp;&nbsp;&nbsp;print("outer")  
&nbsp;&nbsp;&nbsp;&nbsp;inner()

内部函数inner不能在外部直接使用，会抛出NameError异常，因为它在函数外部不可见，其实，**inner不过就是一个标识符，就是一个函数outer内部定义的变量而已。**  

##### 嵌套结构的作用域  

对比下面嵌套结构，代码执行的效果  
![](images\img1.png)
*  外层函数在内部作用域可见
* 内层函数inner中，如果定义可o = 97，相当于当前函数inner作用域中**重新定义了一个新的变量o**，但是，**这个o并不能覆盖外部作用域outer2中的变量o**。只不过对于inner函数来说，其只能可见自己作用域中定义的变量o了  

一个赋值语句的问题  
再看下例  
![](images\img2.png)  
原因分析：  
* x += 1 其实是 x = x + 1
* 相当于在foo内部定义一个局部变量x，那么foo内部所有x都是这个局部变量x了
* x = x + 1 相当于使用了局部变量x，但是这个x还没有完成赋值，就被右边拿来做加1操作了  

如何解决这个常见问题？  

##### global 语句
使用global关键字的变量，将foo内的x声明为使用**外部的全局作用域**中定义的x  
全局作用域中必须有x的定义  
**使用了global，foo中的x不再是局部变量了，它是全局变量**  

总结  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;x += 1 这种是特殊形式产生的错误原因？ 先引用后赋值，而python动态语言是赋值才算定义，才能被引用。解决办法，在这条语句前增加x = 0之类的赋值语句，或者使用global告诉内部作用域，取全局作用域查找变量定义  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;内部作用域使用x = 10 之类的赋值语句会重新定义局部作用域使用的变量x，但是，一旦这个作用域中使用global声明x为全局的，那么x = 5相当于在全局作用域的变量 x 赋值  

global使用原则  
&nbsp;&nbsp;&nbsp;&nbsp;外部作用域变量会在内部作用域可见，但也不要在这个内部的局部作用域中直接使用，因为函数的目的就是为了封装，尽量与外界隔离  
&nbsp;&nbsp;&nbsp;&nbsp;如果函数需要使用外部全局变量，请尽量使用函数的形参定义，并在调用传实参解决  
&nbsp;&nbsp;&nbsp;&nbsp;一句话：**不用global**，学习它就是为了深入理解变量作用域

### 闭包  
**自由变量**：未在本地作用域中定义的变量，例如定义在内层函数外的外层函数的作用域中的变量  

**闭包**：就是一个概念，出现在嵌套函数中，指的是**内层函数引用到了外层函数的自由变量**，就形成了闭包。很多语言都有这个概念，最熟悉就是JavaScript  

##### nonlocal语句
nonlocal : 将变量标记为不在本地作用域定义，而是在**上级的某一级局部作用域**中定义，但**不能是全局作用域**中定义。  

![](images\img3.png)  
count 是外层函数的局部变量，被内部函数引用。  
内部函数使用nonlocal关键字声明count变量在上级作用域而非本地作用域中定义。  
代码中内层函数引用外部局部作用域中的自由变量，形成闭包。  

#### 变量名解析原则LEGB
* Local，本地作用域，局部作用域的local命名空间。函数调用时创建，调用结束消亡
* Enclosing，python2.2时引入了嵌套函数，实现了闭包，这个就是嵌套函数的外部函数的命名空间
* Global，全局作用域，即一个模块的命名空间。模块被import时创建，解析器退出时消亡
* Build-in，内置模块的命名空间，生命周期从python解释器启动时创建到解释器退出时消亡。例如print(open),print和open都是内置的变量

所以一个名词的查找顺序就是LEGB
![](images\img4.png)  

##### 函数的销毁
定义一个函数就是生成一个函数对象，函数名指向的就是函数对象。  
可以使用del语句删除函数，使其引用计数减1。  
可以使用同名标识符覆盖原有定义，本质上也是使其引用次数减1。  
python程序结束时，所有对象销毁。  
函数也是对象，也不例外，是否销毁，还是看引用计数是否减为0。
***
### 递归函数
递归Recursion  

递归要求：递归一定要求退出条件，递归调用一定要执行到这个退出条件。没有退出条件的递归调用，就是无限调用  
递归调用的深度不宜过深：python对递归调用的深度做了限制，以保护解释器，超过递归深度限制，抛出RecursionError：maxinum recursion depth exceeded超出最大深度  

递归的性能  

循环稍微复杂一些，但是只要不是死循环，可以多次迭代直至算出结果  
递归还有深度限制，如果递归复杂，函数反复压栈，栈内存很快就溢出了  
和循环比较，性能相近，所以并不是说递归一定效率低下，但是递归有深度限制  

间接递归  

间接递归，是通过别的函数调用了函数自身  
但是，如果构成了循环递归调用是非常危险的，但是往往这种情况在代码复杂的情况下，还是可能发生这种调用。要用代码的规范来避免这种递归调用的发生  

递归总结  
* 递归式一种很自然的表达，符合逻辑思维
* 递归相对运行效率低，每一次调用函数都要开辟栈帧
* 递归有深度限制，如果递归层次太深，函数反复压栈，栈内存很快就溢满了
* 如果式有限次数的递归，可以使用递归调用，或者使用循环代替，循环代码稍微复杂一些，但是只要不是死循环，可以多次迭代直至算出结果
* 绝大多数递归，都可以使用循环实现
* 即使递归代码很简洁，但是**能不用则不用**递归
***
### 匿名函数
匿名：隐藏名字，即没有名称  
匿名函数：没有名字的函数  

#### Lambda表达式
python中，使用Lambda表达式构建匿名函数。
* 使用lambda关键字定义匿名函数，格式为 lambda[参数列表]：表达式
* 参数列表不需要小括号。无参就不写参数
* 冒号用来分割参数列表和表达式部分
* 不需要使用return。表达式的值，就是匿名函数的返回值。表达式中不能出现等号
* lambda表达式(匿名函数)只能写在一行上，也称为单行函数  

匿名函数往往用在为高价函数传参时，使用lambda表达式，往往能简化代码
>lambda x: x ** 2  # 定义  
(lambda x: x ** 2)(4) # 调用  
foo = lambda x,y: (x+y) ** 2 # 定义函数，不推荐，不如直接定义函数  
foo(1,2)  
\#等价于  
def foo(x,y):  
&nbsp;&nbsp;&nbsp;&nbsp;return (x+y) ** 2
***
### 生成器
生成器generator
* 生成器指的是生成器对象，可以由生成器表达式得到，也可以使用yield关键字得到一个生成器函数，调用这个函数得到一个生成器对象
* 生成器对象，是一个可迭代对象，是一个迭代器
* 生成器对象，是延迟计算、惰性求值的  

生成器函数  
&nbsp;&nbsp;&nbsp;&nbsp;函数体中包含yield语句的函数，就是生成器函数，调用后返回生成器对象  
&nbsp;&nbsp;&nbsp;&nbsp;普通函数调用，函数会立即执行知道执行完毕  
&nbsp;&nbsp;&nbsp;&nbsp;生成器函数调用，并不会立即执行函数体，而是需要使用next函数来驱动生成器函数执行后获得的生成器对象  
&nbsp;&nbsp;&nbsp;&nbsp;生成器表达式和生成器函数都可以得到生成器对象，只不过生成器函数可以写的更加复杂的逻辑  

&nbsp;&nbsp;&nbsp;&nbsp;包含yield语句的生成器函数调用后，生成生成器对象的时候，**生成器函数的函数体不会立即执行**  
&nbsp;&nbsp;&nbsp;&nbsp;next(generator)会从函数的当前位置向后执行到之后碰到的第一个yield语句，会弹出值，并暂停函数执行  
&nbsp;&nbsp;&nbsp;&nbsp;再次调用next函数，和上一条一样的处理过程  
&nbsp;&nbsp;&nbsp;&nbsp;继续调用next函数，生成器函数如果结束执行了(显示或隐式调用了return语句)，会抛出stopiteration异常  

##### 生成器的执行
* 在生成器函数中，可以多次yield，每执行一次yield后会暂停执行，把yield表达式的返回
* 再次执行会执行到下一个yield语句又会暂停执行
* return语句依然可以终止函数运行，但return语句的返回值不能被获取到
* return会导致当前函数返回，无法继续执行，也无法继续获取下一个值，抛出stopiteration异常
* 如果函数没有显示的return语句，如果生成器函数执行到结尾(相当于执行了return None)，一样会抛出stopiteration异常

#### 生成器应用
无限循环  
>def counter():  
&nbsp;&nbsp;&nbsp;&nbsp;i = 0  
&nbsp;&nbsp;&nbsp;&nbsp;while True:  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;i += 1  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;yield i  
c = counter()  
print(next(c)) # 打印 1  
print(next(c)) # 打印 2  
\# 每次打印+1

计数器
>修改上例  
def inc():  
&nbsp;&nbsp;&nbsp;&nbsp;def counter():  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;i = 0  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;while True:  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;i += 1  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;yield i  
&nbsp;&nbsp;&nbsp;&nbsp;c = counter()  
&nbsp;&nbsp;&nbsp;&nbsp;def inner():  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;return next(c)  
&nbsp;&nbsp;&nbsp;&nbsp;return inner  
foo = inc()  
print(foo()) # 打印 1  
print(foo()) # 打印 2

斐波那契数列
>def fib():  
&nbsp;&nbsp;&nbsp;&nbsp;x = 0  
&nbsp;&nbsp;&nbsp;&nbsp;y = 1  
&nbsp;&nbsp;&nbsp;&nbsp;while True:  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;yield y  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;x, y = y, x + y  
foo = fib()  
for i in range(101):  
&nbsp;&nbsp;&nbsp;&nbsp;print(next(foo))

生成器交互  
![](images\img5.png)  
调用send方法，就可以把send的实参传给yield语句做结果，这个结果可以在等式右边被赋值给其他变量  
send和next一样可以推动生成器启动并执行  

协程Coroutine  
* 生成器的高级用法
* 它比进程、线程轻量级，是在用户空间调度函数的一种实现
* python3 asyncio就是协程实现，已经加入到标准库
* python3.5 使用async、 await关键字直接原生支持协程
* 协程调度器实现思路  
有两个生成器A、B  
next(A),A执行到了yield语句暂停，然后去执行next(B),B执行到yield语句也暂停，然后再次调用next(A),再调用next(B),周而复始，就实现了调度的效果  
可以引入调度的策略来实现切换的方式
* 协程是一种非抢占式调度
***
