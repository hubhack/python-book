## 字符串
字符串是一个个字符组成的有序的序列，是字符的集合;是使用单引号、双引号、三引号引住的字符序列;字符串是**不可变**对象。从python3起，字符串就是Unicode类型. 
##### 字符串定义 初始化

```
举例:
s1 = 'string' 
s2 = "string2"
s3 = '''this's a "String" '''
s4 = 'hello \n kugou.com' 
s5 = r"hello \n kugou.com" 
s6 = 'c:\windows\nt' 
s7 = R"c:\windows\nt" 
s8 = 'c:\windows\\\nt'
name = 'tom';age = 20 
s9 = f'{name},{age}' 3.6支持f前缀  
sql = """select * from user where name = 'tom' """
```

##### 字符串元素访问----下标
字符串支持使用索引访问 

```python
sql = "select * from user where name = 'tom' "  
sql[4] = 'c'
```

字符串是有序的字符集合，字符序列
字符串是可迭代的

##### 字符串join连接
“string”.join(iterable) -> str 
将可迭代对象连接起来，使用string作为分隔符 
可迭代对象本身元素都是字符串 
返回一个新字符串  

字符串 + 连接  
> \+ -> str  
>
> 将两个字符串连接一起 
> 返回一个新字符串  

字符串分割  

分割字符串的方法分为2类 
split系 
将字符串按照分隔符分割成若干字符串，并返回列表  

>split(sep = None, maxsplit = -1) -> list of strings 
从左至右 
sep 指定分割字符串，缺省的情况下空白字符串作为分隔符 
maxsplit指定分割的次数，-1表示遍历整个字符串 
rsplit(sep = None, maxsplit = -1) -> list of strings 
从右至左 
sep 指定分割字符串，缺省的情况下空白字符串作为分隔符 
maxsplit指定分割的次数，-1表示遍历整个字符串 
splitlines([keepends]) -> list of strings 
按照行来切分字符串 
keepends指的是是否保留行分隔符 
行分隔符包括\n、\r\n、\r等

partition系 
将字符串按照分隔符分割成2段，返回这2段和分隔符的元组  

>partition(sep) -> (head, sep, tail) 
从左至右，遇到分隔符就把字符串分割成两部分，返回头、分隔符、尾三部分的三元组；没有找到分隔符，就返回头、2个空元素的三元组 
sep 分割字符串，必须指定 
rpartition(sep) -> (head, sep, tail) 
从右至左，遇到分隔符就把字符串分割成两部分，返回头、分隔符、尾三部分的三元组；没有找到分隔符，就返回头、2个空元素的三元组  

字符串大小写  

upper( )  全大写 
lower( )  全小写 
大小写，做判断的时候用 
swapcase( )  交换大小写

字符串排序  

title( ) -> str 
标题的每个单词都大写 
capitalize( ) - > str 
首个单词大写 
center(width[,fillchar]) -> str 
width 打印宽度 
fillchar 填充的字符 
zfill(width) -> str 
width 打印宽度，居右，左边用0填充 
ljust(width,[,fillchar]) -> str 
左对齐 
rjust(width,[,fillchar]) -> str 
左对齐  

##### 字符串修改
>replace(old,new[,count]) -> str 
字符串中找到匹配替换为新字串，返回新字符串 
count表示替换几次，不指定就是全部替换 
strip([chars]) -> str 
从字符串两端去除指定的字符集chars中的所有字符 
如果chars没有指定，去除两端的空白字符 
lstrip([chars]) -> str 
从左开始 
rstrip([chars]) -> str 
从右开始  

##### 字符串查找  
>find(sub[,start[,end]]) -> int 
>在指定的区间[start,end),从左至右，查找子串sub。找到返回索引，没找到返回-1 
>rfind(sub[,start[,end]]) -> int 
>在指定的区间[start,end),从右至左，查找子串sub。找到返回索引，没找到返回-1 
>index(sub[,start[,end]]) -> int 
>在指定的区间[start,end),从左至右，查找子串sub。找到返回索引，没找到抛出异常ValueError 
>
>rindex(sub[,start[,end]]) -> int 
>在指定的区间[start,end),从右至左，查找子串sub。找到返回索引，没找到抛出异常ValueError 
>count(sub[,start[,end]]) -> int 
>在指定的区间[start,end),从左至右，统计字串sub出现的次数 
>len(string) 
>返回字符串的长度，即字符的个数  

时间复杂度 
index和count方法都是O(n) 
随着列表数据规模的增大，而效率下降  

##### 字符串判断
>endswith(suffix[,start[,end]]) -> bool 
在指定的区间[start,end),字符串是否是suffix结尾 
startswith(prefix[,start[,end]]) -> bool 
在指定的区间[start,end),字符串是否是prefix开头

字符串判断is系列  
>isalnum( ) -> bool 是否是字母和数字组成 
isapha( ) 是否是字母 
isdecimal( ) 是否只包含十进制数字 
isdigit( ) 是否全部数字(0~9) 
isidentifier( ) 是不是字母和下划线开头，其他都是字母、数字、下划线 
islower( )是否都是小写 
isupper( ) 是否全部大写 
isspace( ) 是否只包含空白字符

##### 字符串格式化
字符串的格式化是一种拼接字符串输出样式的手段，更灵活方便 
join拼接只能使用分隔符，且要求被拼接的是可迭代对象且其元素是字符串  

+ 拼接字符串还算方便，但是非字符串需要先转换为字符串才能拼接  

在2.5版本之前，只能使用printf style风格的print输出 
printf-style formatting,来自于C语言的printf函数 
格式要求 
占位符:使用 % 和格式字符组成，例如%s、%d等 
s调用str( ), r会调用repr( )。所有对象都可以被这两个转换 
占位符中还可以插入修饰字符，例如%03d表示打印3个位置，不够前面补零 
format % values，格式字符串和被格式的值之间使用%分隔 
values只能是一个对象，或是一个与格式字符串占位符数目相等的元组，或一个字典  

>printf-style formatting举例 
"I am %03d" %(20,) 
'I like %s.' %'Python' 
"%3.2f% % 0x%x %#X" %(89.7654,10,256) 
"I am %-5d" %(20,)
##### format函数格式化字符串语法----Python鼓励使用
>"{}{xxx}".format(*args,**kwargs) -> str

args是可变位置参数，是一个元组 
kwargs是可变关键字参数，是一个字典 
花括号表示占位符 
{}表示按照顺序匹配位置参数，{n}表示去位置参数索引为n的值 
{xxx}表示在关键字参数中搜索名称一致的 


位置参数 
"{}:{}".format('192.168.1.100',8888),这就是按照位置顺序用位置参数替换前面的格式字符串的占位符中.  

关键字参数或命名参数 
"{server}{1}:{0}".format(8888,'192.168.1.100',server='Web Server Info:'),位置参数按照序号匹配，关键字参数按照名词匹配.  

访问元素 
"{0[0]}.{0[1]}".format(('kugou','com'))

对象属性访问 
Point = namedtuple('Point','x,y') 
p = Point(4,5)


**********
#### bytes、bytearray
bytes、bytearray是python3中引入的两个新类型，bytes是不可变字节序列 ; byterray是字节数组，是可变的。  

##### 字符串与bytes  
字符串是字符组成的有序序列，字符可以使用编码来理解 
bytes是字节组成的有序的不可变序列 
byterray是字节组成的有序的可变序列  

##### 编码与解码  
字符串按照不同的字符集编码encode返回字节序列bytes 
encode(encoding='utf-8',errors=''strict) -> bytes 
字节序列按照不同的字符集解码decode返回字符串 
bytes.decode(encoding="utf-8",errors=""strict) -> str 
bytearray.decode(encoding="utf-8",errors="strict") -> str  

##### bytes定义
* bytes( ) 空bytes  
* bytes(int) 指定字节的bytes，被0填充  
* bytes(iterable_of_ints) -> bytes[0,255]的int组成的可迭代对象  
* bytes(string,encoding[,errors]) -> bytes 等价于string.encode( )  
* bytes(bytes_or_buffer) -> immutable copy of bytes_or_buffer 从一个字节序列或者buffer复制处一个新的不可变的bytes对象
* 使用b前缀定义 
只允许基本ASCII使用字符形式 b'abc9' 
使用16进制表示  b"\x41\x61"  

##### bytes操作
和str类型类似，都是不可变类型，所以方法很多都一样。只不过bytes的方法，输入是bytes，输出是byres 
b'abcdef'.replace(b'f',b'k') 
b'abc'.find(b'b') 
类方法 bytes.fromhex(string) 
string必须是2个字符的16进制的形式，'6162 6a 6b',空格将被忽略 
bytes.fromhex('6162 09 6a 6b00') 
hex( ) 
返回16进制表示的字符串 
'abc'.encode( ).hex() 
索引 
b'abcdef'[2]返回该字节对应的数，int类型  

##### bytearray定义  
* bytearray( ) 空bytearray
* bytearray(int) 指定字节的bytearray，被0填充
* bytearray(interable_of_ints) -> bytearray[0,255]的int组成的可迭代对象
* bytearray(string,encoding[,errors]) -> bytearray 近似string.encode( )，不过返回可变对象
* bytearray(bytes_or_buffer) 从一个字节序列或者buffer复制一个新的可变的bytearray对象
* 注意：b前缀定义的类型是bytes类型

##### bytearray操作
和bytes类型的方法相同 
bytearray(b'abcdef').replace(b'f',b'k') 
byteearray(b'abc').find(b'b') 
类方法bytearray.fromhex(string) 
string必须是2个字符的16进制的形式，'6162 6a 6b',空格将被忽略 
bytearray.fromhex('6162 09 6a 6b00') 
返回16进制表示的字符串 
bytearray('abc'.encode()).hex( ) 
索引 
bytearray(b'abcdef')[2]返回该字节对应的数,int类型

>append(int) 尾部追加一个元素 
insert(index,int) 在指定索引位置插入元素 
extend(itearable_of_ints)将一个可迭代的整数集合追加到当前bytearray 
pop(index = -1) 从指定索引上移元素，默认从尾部移除 
remove(value) 找到第一个value移除，找不到抛ValueError异常 
注意： 上述方法需要使用int类型，值在[0,255] 
clear( ) 清空bytearray 
reverse( ) 翻转bytearray,就地修改  

##### int和bytes
int.from_bytes(byres,byteprder) 
将一个字节数组表示成整数 
int.to_bytes(length,byteorder) 
byteorder字节序 
将一个整数表达成一个指定长度的字节数组

****