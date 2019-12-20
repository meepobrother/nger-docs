## Head 方法装饰器
> 用于声明`Head`方法

```ts
@Controller('/')
export class UserController {
    @Head('/login')
    loginHead() {}
}
```