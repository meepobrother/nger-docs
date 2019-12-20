## Patch 方法装饰器
> 用于声明`Patch`方法


```ts
@Controller('/')
export class UserController {
    @Patch('/:id')
    loginOptions(@Param(`id`) id: string) {}
}
```