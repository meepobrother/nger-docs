## Delete 方法装饰器
> 用于声明`Delete`方法


```ts
@Controller('/')
export class UserController {
    @Delete('/login')
    deleteUser() {}
}
```