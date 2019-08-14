

---



key-value数据库memcached,就是为了快基于内存实现,用哈希表.把数据拿出来,lcucache做缓存的, 可以做buffer 是队列的.一般情况下, 队列要考虑持久化, redis实现了持久化.

ps aux | grep redis

权限chown redis.redis -R data/

systemd 有监管作用

权限问题, 

---

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





