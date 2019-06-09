
### 列表list
一个队列，一个排列整齐的队伍 .
列表内的个体称作元素，由若干元素组成列表 .
元素可以是任意对象（数字、字符串、对象、列表等 .
列表内元素由顺序，可以使用索引 .列表是线性的数据结构 .
使用 [ ] 表示 ,列表是可变的  . 

列表list定义 初始化 
list( ) - > new empty list 
list(iterable) - > new list initlized from iterable's items  

列表不能一开始就定义大小

```
lst = list( ) 
lst = [ ] 
lst = [2, 6, 9, 'ab'] 
lst = list(range(5))
```

##### 列表索引访问  

索引：也叫下标，正索引：从左至右，从0开始，为列表中每一个元素标号；负索引：从右开始，从-1开始。正负索引不可以超界，否则会引发异常IndexError，为了理解方便，可以认为列表是从左至右排列，左边是头部，右边是尾部，左边是下界，右边是上界  
>list[index]  index就索引，使用中括号访问  

##### 列表查询

```
index(value,[start,[stop]])  
通过值value，从指定区间查找列表内的元素是否匹配  
匹配第一个就立即返回索引  
匹配不到，抛出异常ValueError  
count(value)  
返回列表中匹配value的次数  
时间复杂度  
index和count方法都是O(n)  
随着列表数据规模的增大，而效率下降  
返回列表元素的个数  
len( )  
索引访问修改  
list[index] = value  索引不能超界 
```

##### 列表增加、插入元素

```
append(object) - > None  
列表尾部追加元素，返回None  
返回None就意味着没有新的列表产生，就地修改  
时间复杂度是O(1)  
insert(index,object) - > None  
在指定的索引index处插入元素object  
返回None就意味着没有新的列表产生，就地修改  
时间复杂度是O(n)  
索引超越上界，尾部增加，索引超越下届，头部追加  
extend(iteratable) - > None  
将可迭代对象的元素追加进来，返回None  
就地修改  
 \+ - > list  
 连接操作，将两个列表连接起来  
 产生新的列表，原列表不变  
 本质上调用的魔术方法_add_()方法  
 \* - > list  
 重复操作，将本列表元素重复n次，返回新的列表
```

##### 列表删除元素

```
remove(value) - > None  
从左至右查找第一个匹配value的值，移除该元素，返回None  
就地修改  
时间复杂度是O(n)  
pop([index]) - > item  
不指定索引index,就从列表尾部弹出一个元素  
指定索引index，就从索引处弹出一个元素，索引超界抛出IndexError错误  
clear( ) - > None  
清楚列表所有元素，剩下一个空列表
```

##### 列表其他操作

```
reverse( ) - > None  
将列表元素反转，返回None  
就地修改  
sort(key=None,reverse=Flase) - > None  
对列表元素进行排序，就地修改，默认升序  
reverse为True，反转，降序  
key一个函数，指定key如何排序  
lst.sort(key=function)
```

##### 列表复制

```
shadow copy  
影子拷贝，也叫浅拷贝，遇到引用类型，只是复制了一个引用而已，等于复制了一个地址，如果地址中储存的值改变的话，被复制出去的值都会改变  
深拷贝  
copy模块提供了deepcopy,深度拷贝就是给值复制过去，原来的怎么变化，复制走的值都不会改变。

```



****