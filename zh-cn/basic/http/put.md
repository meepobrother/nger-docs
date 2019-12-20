## Put 方法装饰器
> 用于声明`Put`方法

```ts
@Controller('/')
export class UserController {
    @Put('/:id')
    loginOptions(@Param(`id`) id: string) {}
}
```