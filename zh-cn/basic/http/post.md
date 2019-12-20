## Post方法装饰器
> 用于声明`Post`方法

```ts
@Controller('/')
export class UserController {
    @Post('/:id')
    loginOptions(@Param(`id`) id: string) {}
}
```