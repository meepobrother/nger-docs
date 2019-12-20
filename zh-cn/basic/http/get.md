## Get 方法装饰器
> 用于声明`Get`方法


```ts
@Controller('/')
export class UserController {
    @Get('/login')
    loginPage() {}
}
```