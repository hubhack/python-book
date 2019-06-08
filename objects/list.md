## python内置数据结构
### 分类
数值型：int、float、complex、bool  
序列对象：字符串 str、列表 list、tuple  
键值对：集合 set、字典 dict  

### 数值型
1. int 整型，python3的int就是长整型，且没有大小限制，受限于内存区域的大小
2. float 浮点型，由整数部分和小数部分组成。支持十进制和科学计数法表示。C的双精度实现
3. complex 复数，由实数和虚数部分组成，实数和虚数部分都是浮点数
4. bool 布尔型，int的子类，仅有两个实例True、False对应1和0，可以和整数直接运算  

类型转换
>int(x) 返回一个整数  
float(x) 返回一个浮点数  
complex(x)、complex(x,y)返回一个复数  
bool(x) 返回布尔值 

数字的处理函数
>round( ) 四舍六入五取偶  
floor( ) 向下取整  
ceil( ) 向上取整  
int( ) 取整数部分  
// 整除且向下取整  
min( ) 取最小值  
max( ) 取最大值  
pow(x,y) 等于x**y  
math.sqrt(x) 返回数字x的平方根  

进制函数，返回值是字符串
>bin( )  返回二进制  
oct( )  返回八进制  
hex( ) 返回十六进制

类型判断  
type( ),返回类型，而不是字符串  
isinstance(obj,class_or_tuple),返回布尔值  

ex:  
>type('abc')  
isinstance(6,str)  
isinstance(6,(str,bool,int))

### 列表list
一个队列，一个排列整齐的队伍  
列表内的个体称作元素，由若干元素组成列表  
元素可以是任意对象（数字、字符串、对象、列表等）  
列表内元素由顺序，可以使用索引  
线性的数据结构  
使用 [ ] 表示  
列表是可变的   

列表list定义 初始化  
list( ) - > new empty list  
list(iterable) - > new list initlized from iterable's items  

列表不能一开始就定义大小
>lst = list( )  
lst = [ ]  
lst = [2, 6, 9, 'ab']  
lst = list(range(5))

##### 列表索引访问  

索引：也叫下标，正索引：从左至右，从0开始，为列表中每一个元素标号；负索引：从右开始，从-1开始。正负索引不可以超界，否则会引发异常IndexError，为了理解方便，可以认为列表是从左至右排列，左边是头部，右边是尾部，左边是下界，右边是上界  
>list[index]  &nbsp;&nbsp;&nbsp;index就索引，使用中括号访问  

##### 列表查询
>index(value,[start,[stop]])  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;通过值value，从指定区间查找列表内的元素是否匹配  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;匹配第一个就立即返回索引  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;匹配不到，抛出异常ValueError  
count(value)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;返回列表中匹配value的次数  
时间复杂度  
&nbsp;&nbsp;&nbsp;&nbsp;index和count方法都是O(n)  
&nbsp;&nbsp;&nbsp;&nbsp;随着列表数据规模的增大，而效率下降  
返回列表元素的个数  
&nbsp;&nbsp;&nbsp;&nbsp;len( )  
索引访问修改  
&nbsp;&nbsp;&nbsp;&nbsp;list[index] = value  &nbsp;&nbsp;索引不能超界  

##### 列表增加、插入元素
>append(object) - > None  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;列表尾部追加元素，返回None  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;返回None就意味着没有新的列表产生，就地修改  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;时间复杂度是O(1)  
insert(index,object) - > None  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;在指定的索引index处插入元素object  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;返回None就意味着没有新的列表产生，就地修改  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;时间复杂度是O(n)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;索引超越上界，尾部增加，索引超越下届，头部追加  
extend(iteratable) - > None  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;将可迭代对象的元素追加进来，返回None  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;就地修改  
 \+ - > list  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;连接操作，将两个列表连接起来  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;产生新的列表，原列表不变  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;本质上调用的魔术方法_add_()方法  
 \* - > list  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;重复操作，将本列表元素重复n次，返回新的列表

##### 列表删除元素
>remove(value) - > None  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;从左至右查找第一个匹配value的值，移除该元素，返回None  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;就地修改  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;时间复杂度是O(n)  
pop([index]) - > item  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;不指定索引index,就从列表尾部弹出一个元素  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;指定索引index，就从索引处弹出一个元素，索引超界抛出IndexError错误  
clear( ) - > None  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;清楚列表所有元素，剩下一个空列表

##### 列表其他操作
>reverse( ) - > None  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;将列表元素反转，返回None  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;就地修改  
sort(key=None,reverse=Flase) - > None  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;对列表元素进行排序，就地修改，默认升序  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;reverse为True，反转，降序  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;key一个函数，指定key如何排序  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;lst.sort(key=function)

##### 列表复制
shadow copy  
&nbsp;&nbsp;&nbsp;&nbsp;影子拷贝，也叫浅拷贝，遇到引用类型，只是复制了一个引用而已，等于复制了一个地址，如果地址中储存的值改变的话，被复制出去的值都会改变  
深拷贝  
&nbsp;&nbsp;&nbsp;&nbsp;copy模块提供了deepcopy,深度拷贝就是给值复制过去，原来的怎么变化，复制走的值都不会改变。

##### 随机数
random模块   
>randint(a,b)  
&nbsp;&nbsp;&nbsp;&nbsp;返回[a,b]之间的整数  
choice(seq)  
&nbsp;&nbsp;&nbsp;&nbsp;从非空序列的元素中随机挑选一个元素，比如random.choice(range(10)),从0到9中随机挑选一个整数  
randrange([start,]stop[,step])  
&nbsp;&nbsp;&nbsp;&nbsp;从指定范围内，按指定基数递增的集合中获取一个随机数，基数缺省值为1  
random.shuffle(list) - > None   
&nbsp;&nbsp;&nbsp;&nbsp;就地打乱列表元素  
sample(population,k)  
&nbsp;&nbsp;&nbsp;&nbsp;从样本空间或总体(序列或者集合类型)中随机取出k个不同的元素，返回一个新的列表

****