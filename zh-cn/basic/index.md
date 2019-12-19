## 基础概念

### 类
| 名称                                          | 说明       |
| --------------------------------------------- | ---------- |
| [Injector](/zh-cn/basic/injector.md)          | 注入类     |
| [PlatformRef](/zh-cn/basic/injector.md)       | 平台       |
| [NgModuleRef](/zh-cn/basic/injector.md)       | 模块       |
| [ControllerFactory](/zh-cn/basic/injector.md) | 控制器工厂 |
| [ErrorHandler](/)                             | 错误处理   |
| [Config](/)                                   | 配置       |
| [Logger](/)                                   | 日志       |
| [PipeTransform](/)                            | 管道       |

### 类装饰器
| 名称                                      | 说明   |
| ----------------------------------------- | ------ |
| [Module/NgModule](/zh-cn/basic/module.md) | 模块   |
| [Controller](/zh-cn/basic/controller.md)  | 控制器 |
| [Injectable](/zh-cn/basic/injectable.md)  | 服务   |

### 方法装饰器
| 名称                                                 | 说明                      |
| ---------------------------------------------------- | ------------------------- |
| [Get](/zh-cn/basic/http/get.md)                      | Get请求                   |
| [Post](/zh-cn/basic/http/post.md)                    | Post请求                  |
| [Put](/zh-cn/basic/http/put.md)                      | Put请求                   |
| [Delete](/zh-cn/basic/http/delete.md)                | Delete请求                |
| [Head](/zh-cn/basic/http/head.md)                    | Head请求                  |
| [Options](/zh-cn/basic/http/options.md)              | Options请求               |
| [All](/zh-cn/basic/http/all.md)                      | All请求                   |
| [Head](/zh-cn/basic/http/head.md)                    | Head请求                  |
| [Query](/zh-cn/basic/graphql/query.md)               | graphql query 请求        |
| [Mutation](/zh-cn/basic/graphql/mutation.md)         | graphql mutation 请求     |
| [Subscription](/zh-cn/basic/graphql/subscription.md) | graphql subscription 请求 |

### 参数装饰器
| 名称                                    | 语法                     |
| --------------------------------------- | ------------------------ |
| [Inject](/zh-cn/basic/inject.md)        | 注入                     |
| [Body](/zh-cn/basic/http/body.md)       | Post请求Body内容         |
| [Query](/zh-cn/basic/http/query.md)     | 连接中Query内容获取      |
| [Param](/zh-cn/basic/http/param.md)     | 连接中Path Param内容获取 |
| [Req](/zh-cn/basic/http/req.md)         | 请求获取                 |
| [Res](/zh-cn/basic/http/res.md)         | 响应                     |
| [Next](/zh-cn/basic/http/next.md)       | 下一个                   |
| [Headers](/zh-cn/basic/http/headers.md) | 头部内容获取             |
| [Session](/zh-cn/basic/http/session.md) | Session内容获取          |
| [Cookies](/zh-cn/basic/http/cookies.md) | Cookies内容获取          |

### 属性装饰器

| 名称          | 语法     |
| ------------- | -------- |
| [InjectPro]() | 属性注入 |


### 接口
| 名称                        | 简介 |
| --------------------------- | ---- |
| [ClassHandler]()            |      |
| [PropertyHandler]()         |      |
| [MethodHandler]()           |      |
| [ParameterHandler]()        |      |
| [ControllerMethodHandler]() |      |
| [ControllerClassHandler]()  |      |
| [CanActivate]()             |      |
| [CanLoad]()                 |      |
| [OnModuleInit]()            |      |
| [OnDestroy]()               |      |

### Token
| 名称                     | 简介           |
| ------------------------ | -------------- |
| REQUEST_ID               | 当前请求id     |
| REQUEST                  | 当前请求       |
| RESPONSE                 | 当前响应       |
| NEXT                     | 当前Next       |
| ROUTER                   | 当前路由       |
| PATH                     | 路径           |
| RESPONSE_HANDLER         | 处理返回结果   |
| APP_ID                   | 应用 id        |
| APP_INITIALIZER          | 应用初始化钩子 |
| PLATFORM_INITIALIZER     | 平台初始化钩子 |
| PLATFORM_ID              | 平台Id         |
| LOGGER_LEVEL             | 日志等级       |
| ALLOW_MULTIPLE_PLATFORMS | 允许多平台运行 |
| CONTEXT                  |                |
