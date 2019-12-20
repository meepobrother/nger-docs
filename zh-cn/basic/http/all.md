## All 方法装饰器
> 用于声明`All`方法


```ts
@Controller('/')
export class UserController {
    @All('/login')
    login() {}
}
```