### mongodb

它是由c++编写的分布式文档数据库
内部使用类似json的bson格式.
中文手册https://www.w3cschool.cn/mongodb/
安装https://www.mongodb.com/download-center/community
windowns下载官方zip, 解压即可使用.

| 组件                | 文件名                                                     |
| ------------------- | ---------------------------------------------------------- |
| Server              | mongod.exe                                                 |
| Router              | mongos.exe                                                 |
| Client              | mongo.exe                                                  |
| Monitoring          | mongostat.exe, mongotop.exe                                |
| ImportExportToos    | mongodump.exe, mongorestore.exe                            |
| MIscellaneoustTools | bsondump.exe,mongofiles.exe, mongooplog.exe, mongoperf.exe |

```
cd /data/mongodb/bin
./mongod.exe

```

选项说明

- --bind_ip ip 逗号分隔ip地址, 默认locallhost
- --bind_ip_all 绑定所有本地ip地址
-  --bind port端口, 默认27017
- --dbpath path数据路径, 缺省为\data\db\. windows下缺省就是当前盘符的根目录.
-  --logpath path 指定日志文件, 替代stdout, 说明默认是控制台打印日志.
-  -f file 指定配置文件, yaml格式
- 注册windows服务
- - --install 注册windows服务
  - --serviceName name服务名称
  - --serviceDisplayName name服务显示名



配置文件

mongodb配置使用yaml格式

嵌套使用缩进完成, 不支持Tab等制表符,支持空格.

冒号后要空格

Yaml参考https://www.w3cschool.cn/iqmrhf/dotvpozt.html

配置http://mongoing.com/docs/reference/configuration-options.html

```
systemlog:
	destination: file
	path: "/bin"
	logAppend: true
storage:
	dbpath:"o://mongodb/db"
	
net:
	bindIP: "127.0.0.1"
	port: 27017

```



选项

- systemLog

- - destination, 缺省是输出到日志std, file 表示输出到文件
  - path, 日志路径
  - logAppend, true 表示在已存在的日志文件追加, 默认flase, 每次启动服务, 重新创建新的日志.

- storage

- - dbpath, 必须指定, mongodb的数据目录

- net

- - bindIP, 缺省绑定到127.0.0.1
  - port, 端口,缺省为27017, 客户端连接使用

  windows下注册为服务的命令如下, 使用了配置文件,

  ```
  mongod.exe -f "/bin/mongodb/bin/mongd.yml" --service mongod --serviceDisplayName mongo --install
  ```

  

```
storage:
	dbpath:"/bin"
net:
	bindIP:"127.0.0.1"
	port:27017
	
```

客户端

客户端连接

```
bin/mongo.exe
```

python连接

```
from pymongo import Mongoclient
client = MongoClient('mongodb://127.0.0.1:27017')
print(client)
db = client['blog']
print(db)

users = db.users
print(users)
```

基本概念

MongoDB中可以创建使用多个库, 但有一些数据库名是保留, 可以直接访问这些有特殊作用的数据库.

- admin: 从权限的角度来看, 这是"root"数据库. 要是将一个用户添加到这个数据库,这个用户自动继承所有数据库的权限,一些特定的服务器命令也只能从这个数据库运行, 比如列出所有的数据库或者关闭服务器.
- local: 这个数据永远不会被复制,可以用来存储咸鱼单台服务器的任意集合.
- config: 当Mongo用于分片设置时, config数据库在内部使用,用于保存分片的相关信息.

插入数据

````
from pymongo.results import InsertOneResult
user1 = {'id': '1', 'name': 'ben', 'age': 20}

x:InsertOneResult = users.insert_one(user1)
print(type(x), x)
# 批量插入
result = users.insert_many([user2, user3])
print(result.inserted_ids)
````

每条数据插入都有一个唯一key, 属性_id唯一标识一个文档. 没有没有显示指明该属性, 会自动生成一个objectldl类型_id属性.

objectld有12字节

- 4字节时间戳
- 3字节机器识别码
- 2字节进程id
- 3字节随机数

文档

每一条记录对应一个文档, 其格式使用bson. bson即binary json.

文档中, 使用键值对

文档中的键值对是有序的.

键是字符串

- 区分大小写, 使用utf-8字符
- 键不能含有\0.这个字符串来表示键字符串的结尾
- 值可以是
  - 字符串, 32位或64位整数, 双精度,时间戳, 布尔型, null
  - 字节数组, bson数组, bson对象














