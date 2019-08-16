### Redis

开源的(bsd协议) , 使用ANSI C编写, 基于内存的且支持持久化, 高性能的Key-Value的NoSQL数据库. 

支持数据结构类型丰富,有如 字符串(strings), 散列(hashes), 列表(lists), 集合(sets)

基于内存,用c写的.弹性扩展,key-value数据库.没有sql概念, 

历史版本https://code.google.com/archive/p/redis/downloads

redis 的数据结构非常丰富, 

hyperloglogs 速度快, 地理空间, 在多少的范围内, gps坐标,memcached 只有string.

节约内存非常重要. 内存碎片化严重, 

编译, 链接

---

单节点安装

----

yum安装redis

```
yum install redis
systemctl start redis
```

---

编译安装

```
yum list | grep redis 
#在epel源里
# 此次用编译安装, 版本3.2

wget http://download.redis.io/releases/redis-3.2.12.tar.gz
tar xzf redis-3.2.12.tar.gz
cd redis-3.2.12
make
# 缺省安装
make install
# 默认安装到/usr/local/bin

# 添加环境变量到~/.bash_profile文件末尾, o添加
export PATH=$PATH:/usr/local/bin
```

redis 服务

systemd服务

```sehll
useradd -r redis
cd /lib/systemd/system

vim redis.service

```

redis.service内容如下

```shell
[Unit]
Description=Redis In-Memory Data Store
After=network.target

[Service]
User=redis
Group=redis
Type=forking
ExecStart=/usr/local/bin/redis-server /etc/redis/redis.conf
ExecStop=/usr/local/bin/redis-cli shutdown
Restart=always

[Install]
WantedBy=multi-user.target
```

[Unit] 表示这是基础信息

Description 是描述

After 是在那个服务后面启动, 一般是网络服务启动后启动

[Service]表示这里是服务信息

ExecStart 是启动服务的命令

ExecStop 是停止服务的指令

[Install]表示这里是安装相关信息

WantedBy 是以哪种方式启动: multi-user.target表明当系统以多用户方式(默认的运行级别)启动时, 这个服务需要被自动运行

### redis数据模型

key是任意可序列化, redis key 需要一个二进制值, 可以用任何二进制作为key值, 可以是简单字符, 可以是简单字符串, 也可以是个jpeg文件的二进制序列, 空字符也是有效key值.

key取值原则

键值不需要太长, 消耗内存, 而且查找这类键值的计算成本较高.

键值不宜过短, 可读性较差.

习惯上key采用'user123:password' 形式,表示用户id为123用户的密码.

### 字符串

字符串是一种最基本简单的redis值类型, 说是字符串, 其实可以是任意可以序列化的数据.

一个字符串类型的值最多能存储512m字节的内容.字符串是最基础的数据类型.

### 位图

位图不是真正的数据类型, 它是定义在字符串类型上, 只不过把字符串按位操作, 

### hash散列

值是field和value组成的map键值对

field和value都是字符串类型.

hash用途

节约内存空间

每创建一个键, 它都会为这个键存储一些附加的管理信息(比如这个键的类型, 这个键最后一次被访问等等)

所以数据库里面的键越多, redis数据库服务器在存储附加管理信息方面耗费的内存就越多, 花在管理数据库键上的cpu时间也会越多.



### redis持久化

持久化: 将数据从掉电易失的内存放到能够永久存储的设备上.

redis服务是使用内存来存储数据, 如果掉电,服务崩溃都会导致redis中数据丢失, 如有必要, 可以持久化数据.

redis持久化方式:rdb(redis db), aof(appendonlyfile)

### RDB

SAVE命令: 阻塞命令,执行期间不响应客户端的请求.

BGSAVE: 非阻塞命令, 执行期间还可以接受并处理客户端请求, 会folk一个子进程创建RDB文件.

### AOF

记录所有的写操作命令, 在服务启动的时候使用这些命令就可以还原数据库.

aof写入机制

aof方式不能保证绝对不丢失数据

目前常见的操作系统中, 执行系统调用write函数,将一些内容写入到某个文件里面时,为了提高效率,系统通常不会直接将内容写入磁盘里面, 而是先将内容放入一个内存缓存区,等到缓存区被填满,或者用户

执行fsync调用和fdataync调用才将存储在缓存区里的内容-真正的写入到磁盘里,  未写入磁盘之前, 数据可能会丢失.

### redis集群

redis集群分为:

主从复制replication

高可用sentinel

集群cluster

### 主从复制

典型的主从模型, 主redis服务称为master, 从redis服务称为slave

redis集群总结

redis集群是一个有多个节点组成的分布式服务集群,它具有复制,高可用和分片特性.

redis的集群没有中心节点, 并且带有复制和故障转义特性,这可用避免单个节点成为性能瓶颈,或者因为某个节点下线而导致整个集群下线.

集群中的主节点负责处理槽(存储数据), 而从节点则是主节点的复制品.

redis集群将整个数据库分为16384个槽,数据库中的每个键都属于16384槽中的其中一个.

集群中每个节点都可以管理槽,当16384个槽都有节点在负责时, 集群进入上线状态,可以执行客户端发送的数据命令.

主节点只会执行和自己负责的槽有关的命令, 当节点接受到不属于自己处理的槽的命令时, 他将会处理指定槽的结点的地址返回给客户端,而客户端会向正确的节点重新发送.