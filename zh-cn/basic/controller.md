## 控制层
> 用于声明控制层

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