## Options 方法装饰器
> 用于声明`Options`方法

```ts
@Controller('/')
export class UserController {
    @Options('/login')
    loginOptions(@Next() next: (err?: Error)=>void) {}
}
```