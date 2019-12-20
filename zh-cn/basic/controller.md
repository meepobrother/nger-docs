## 控制层
> 用于声明控制层
参数
```ts
export interface ControllerOptions {
    path: PathParams; // 路由，非单例
    providers?: (Provider | Provider[])[]; // 依赖，非单例
    useGuards?: Type<any>[];// 守卫，当前作用域下为单例
}
```

### path 路由路径
> 指定Controller路由，可以为Grpc/Graphql/Http等提供服务。

### providers 服务
> 当前路由用到的服务，注意是一次性的。用完即自动注销。

### useGuards 路由
> 用到的路由守卫，一搬用来做权限认证。


```ts
@Controller('/')
export class UserController {

    /**
     * 渲染登录页
     **/
    @Get('/login')
    @Render('index')
    loginPage() {
        return {
            title: ``
        }
    }

    @Post('/login')
    login(@Body('username') username: string,@Body('password') password: string){
        return {
            username,
            password
        }
    }
}
```