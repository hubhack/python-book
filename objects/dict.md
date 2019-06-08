
***
### 字典dict
字典是key-value键值对的数据的集合，和集合一样，是可变的、无序的，dict字典key不重复，是唯一的。  

##### 字典dict定义 初始化
d = dict() 或者 d = {} - > 这是定义一个空字典  

dict(**kwargs) 使用name = value 对初始化一个字典  

dict(iterable,**kwarg)使用可迭代对象和name = value对构造字典，不过可迭代对象的对象必须是一个二元结构  
d = dict(((1,'a',(2,'b'))) 或者 d = dict(([1,'a'],[2,'b']))  

dict(mapping,**kwarg)使用一个字典取构建另一个字典  

d = {'a':10,'b':20,'c':None,'d':[1,2,3]}  

类方法dict.fromkeys(iterable,value)  
d = dict.fromkeys(range(5))  
d = dict.fromkeys(range(5),0)  

##### 字典元素的访问
d[key]  
返回key对应的值value  
key不存在抛出KeyError异常  

get(key[,default])  
返回key对应的值value  
key不存在返回缺省值，如果没有设置缺省值就返回None  

setdefault(key,[default])  
key不存在，添加kv对，value设置为default，并返回defau，如果default没有设置，缺省值为None  

##### 字典增加和修改
d[key] = value  
将key对应的值修改为value  
key不存在添加新的kv对  

update([other]) -> None  
使用另一个字典的kv对更新本字典  
key不存在，就添加  
key存在，覆盖已经存在的key对应的值  
就地修改  

##### 字典删除
pop(key[,default])  
key存在，移除它，并返回它的value  
key不存在，返回给定的default  
default未设置，key不存在则抛出KeyError异常  

popitem()  
移除并返回一个任意的键值对  
字典为empty，抛出KeyError异常  

clear()  
清空字典

##### 字典遍历  
for ... in dict  
遍历key  
* for k in d:  
print(k)  
* for k in d.keys():  
print(k)  

遍历value  
* for k in d:  
print(d[k])  
* for k in d.keys():  
print(d.get(k))
* for v in d.values():  
print(v)  

遍历item，即kv对 
* for item in d.items():  
print(item)
* for item in d.items():  
print(item[0],item[1])
* for k,v in d.items():  
print(k,v)
* for k,_ in d.items():  
print(k)
* for _,v in d.items():  
print(v)  

python3中，keys、values、items方法返回一个类似一个生成器的可迭代对象，不会把函数的返回结果复制到内存中，返回Dictionary view对象，可以使用len()、iter()、in操作，字典的entry的动态的视图，字典变化，试图将反映出这些变化，keys返回一个类set对象，也就是可以看做一个set集合，如果values都可以hash，那么items也可以看作是类set对象。  

python2中，上面的方法会返回一个新的列表，占据新的内存空间。所以python2建议使用iterkeys、itervalues、iteritems版本，返回一个迭代器，而不是返回一个copy。

##### 字典的key
key的要求和set的元素要求一致，set的元素可以就是看作key，set可以看作dict的简化版，hashable可哈希才可以作为key，可以使用hash()测试。

##### defaultdict
collections.defaultdict([default_factory[,...]])  
第一个参数是default_factory,缺省值是None，它提供一个初始化函数。当key不存在的时候，会调用这个工厂函数来生成key对应的value  
构造一个字典，values是列表，为其添加随机个元素

##### OrderedDict
collection.OrderDict([items])  
key并不是按照加入的顺序排列，可以使用OrderDict记录顺序  
有序字典可以记录元素插入的顺序，打印的时候也是按照这个顺序输出打印  
3.6版本的Python的字典就是记录key插入的顺序(IPython不一定由效果)