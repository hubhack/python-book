aiohttp是一个http客户端, 服务端框架.

安装

```shell
pip install aiohttp
```

```python
from aiohttp import web

async def hello(request):
	return web.Response(text= 'hello, world')
```

## 运行简单的Web服务器

为了实现Web服务器，首先创建一个 [请求处理程序](https://aiohttp.readthedocs.io/en/stable/web_quickstart.html#aiohttp-web-handler)。

请求处理程序必须是一个[协程](https://docs.python.org/3/library/asyncio-task.html#coroutine)，它接受一个[`Request`](https://aiohttp.readthedocs.io/en/stable/web_reference.html#aiohttp.web.Request)实例作为其唯一参数并返回一个[`Response`](https://aiohttp.readthedocs.io/en/stable/web_reference.html#aiohttp.web.Response)实例：

```
from aiohttp import web

async def hello(request):
    return web.Response(text="Hello, world")
```

接下来，创建一个[`Application`](https://aiohttp.readthedocs.io/en/stable/web_reference.html#aiohttp.web.Application)实例并在特定的*HTTP方法*和*路径*上注册请求处理程序：

```
app = web.Application()
app.add_routes([web.get('/', hello)])
```

之后，通过[`run_app()`](https://aiohttp.readthedocs.io/en/stable/web_reference.html#aiohttp.web.run_app)调用运行应用程序：

```
web.run_app(app)
```

而已。现在，`http://localhost:8080/`请前往查看结果。

或者，如果您更喜欢*路径装饰器，则*创建*路由表* 并注册[Web处理程序](https://aiohttp.readthedocs.io/en/stable/glossary.html#term-web-handler)：

```
routes = web.RouteTableDef()

@routes.get('/')
async def hello(request):
    return web.Response(text="Hello, world")

app = web.Application()
app.add_routes(routes)
web.run_app(app)
```

两种方式基本上都做同样的工作，区别仅在于你的口味：你喜欢着名的*Django风格*`urls.py`还是 带有闪亮路线装饰的*Flask*。