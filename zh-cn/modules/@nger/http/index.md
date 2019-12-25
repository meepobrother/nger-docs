## @nger/http
<p>
    <a href="https://www.npmjs.com/package/@nger/http">
        <img src="https://img.shields.io/npm/v/@nger/http.svg" alt="Version">
    </a>
    <a href="https://www.npmjs.com/package/@nger/http">
        <img src="https://img.shields.io/npm/l/@nger/http.svg" alt="License">
    </a>
    <a href="https://npmcharts.com/compare/@nger/http?minimal=true">
        <img src="https://img.shields.io/npm/dm/@nger/http.svg" alt="Downloads">
    </a>
</p>

使用时需要依赖其他模块提供`HttpBackend`服务,可注入多个拦截器`HTTP_INTERCEPTORS`

`@nger/http` 中的 `HttpClient` 类为 `nger` 应用程序提供了一个简化的 `API` 来实现 `HTTP` 客户端功能。`HttpClient` 带来的其它优点包括：`可测试性`、`强类型`的请求和`响应对象`、`发起请求`与`接收响应`时的`拦截器`支持，以及更好的、基于可观察（`Observable`）对象的 API 以及流式错误处理机制。


## 准备工作

```ts
@Module({
  imports: [
    HttpModule
  ]
})
export class AppModule {}
```

## 使用
在 `AppModule` 中导入 `HttpModule` 之后，你可以把 `HttpClient` 注入到应用类中，就像下面的 `ConfigService` 例子中这样。

```ts
@Injectable()
export class ConfigService {
  constructor(private http: HttpClient) { }
}
```

## 提供相应服务
```ts
@Controller()
export class DemoController {
    @Get(``)
    getHome() {
        return `welcome to nger home!`
    }
    @Get(`user`)
    getUser(@Query(`id`) id: number, @Query(`name`) name: string) {
        return `welcome to user home! ${id}-${name}`
    }
}
```