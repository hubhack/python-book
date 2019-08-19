### flask
安装
pip install flask
编程快速入门http://docs.jinkan.org/docs/flask/quickstart.html#quickstart
在项目根目录下构建:
1. webapp包目录, 存放flask代码,包内有__init__.py文件
2. templates目录, 存放静态文件
3. static目录, 存放js, css静态文件, 其下建立js目录, 放入jquery, echarts的js文件
4. app.py, 入口文件
基本组成
```
from flask import Flask, Jsonify
# 创建应用
app = Flask('web')
# 路由和视图函数
@app.route('/')
def index():
    return 'hello flask'

@app.route('/json', methods=['GET']) # 列表中指定多个方法
def getjson():
    d = {'a':1, 'b': [1,2,3]}
    return jsonify(d)

# 打印重要属性
print('-' * 30)
print(app.url_map)
```
应用:创建出来提供WEB服务的实例, 也是wsgi的入口
视图函数: 执行内部代码输出响应的内容
路由: 通过route装饰器创建path到视图函数的映射关系.
```
# app.py
from webapp import app

if __name__ == '__main__':
    app.run('0.0.0.0', 80, True)


### 蓝图
Flask中, 基本上都是route装饰器和视图函数的映射, 如果函数很多, 代码结构会非常乱.
蓝图Blueprint, 就是Flask中模块化的技术.
BluePrint构造参数
- name, 蓝图名字, 注册在app的蓝图字典中,用的key.
- import_name, 用来计算蓝图模块所在的路径, 一般写__name__.
- root_path, 指定蓝图模块所在的路径, 如果为None, 使用import_name计算得到.






























