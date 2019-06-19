


### 集set
set翻译为集合，collection翻译为集合类型，是一个大概念。set是**可变的、无序的、不重复**的元素的集合

##### set定义 初始化
set( ) -> 空集合 
set (iterable) -> 新的集合 
s1 = { }  这不是空集合，这个是空字典

##### set的元素
set的元素要求必须可以hash,不可hash的类型右list、set等，set的元素不可以使用索引，set可以迭代。

##### set增加

```
add(elem) 
增加一个元素到set中  
如果元素存在，什么都不做  

update(*others)  
合并其他元素到set集合中来  
参数others必须是可迭代对象  
是就地修改的
```

##### set删除

```
remove(elem)  
从set中移除一个元素  
元素不存在，抛出KeyError异常。  

discard(elem)  
从set中移除一个元素  
元素不存在，什么都不做  

pop() ->item  
移除并返回任意的元素  
空集返回KeyError异常  

clear()  
移除所有元素
```

##### set修改、查询

```
修改  
因为set是无序的、不重复的，修改等于删除再加入新的元素，所以set没有修改操作，要么删除，要么加入新的元素。  

查询  
非线性结构，无法索引  

遍历  
可以迭代所有元素
```

##### set和线性结构

```
线性结构的查询时间复杂度是O(n),即随着数据规模的增大而增加耗时  
set、dict的结构，内部使用hash值作为key，时间复杂度可以做到O(1),查询时间和数据规模无关  

可hash  
数字型int、float、complex，布尔型Ture、False，字符串string、bytes，tuple，None以上都是不可变类型，是可哈希类型。  

set的元素必须是可hash的
```

### 集合
基本概念  

#### 全集  

所有元素的集合。例如实数集，所有实数组成的集合就是全集。  
子集subset和超集superset  
一个集合A所有元素都在另一个集合B内，A是B的子集，B是A的超集  
真子集和真超集  
A是B的子集，且A不等于B，A就是B的真子集，B是A的真超集  

- 并集：多个集合合并的结果  
- 交集：多个集合的公共部分  
- 差集：集合中除去和其他集合公共部分

##### 集合运算
**并集** 
将两个集合A和B的所有元素合并到一起，组成的集合称作集合A与集合B的并集  
union(*others) 
返回和多个集合合并后的新的集合 
| 运算符重载 
等同union 
update(*others) 
和多个集合合并，就地修改 
|= 等同update  

**交集** 
集合A和B，由所有属于A且属于B的元素组成的集合 
intersection(*others) 
返回和多个集合的交集 
&  等同intersection 
intersection_update(*others) 
获取和多个集合的交集，并就地修改 
&= 等同intersection_update  

**差集** 
集合A和B，由所有属于A且不属于B的元素组成的集合 
difference(*others) 
返回和多个集合的差集  

等同difference 
difference_update(*others) 
获取和多个集合的差集并就地修改 
-= 等同difference_update  

**对称差集** 
集合A和B，由所有不属于A和B的交集元素组成的集合 
symmetric_differece(other) 
返回和另一个集合的差集 
^ 等同symmetric_differece 
symmetric_differece_update(other) 
获取和另一个集合的差集并就地修改 
^= 等同symmetric_differece_update  

issubset(other)、<= 
判断当前集合是否是另一个集合的子集 
set1 < set2 
判断set1是否是set2的真子集 
issuperset(other)、>= 
判断当前集合是否是other的超集 
set1 > set2 
判断set1是否是set2的真超集 
isdisjoint(other) 
当前集合和另一个集合没有交集，没有交集，返回True
