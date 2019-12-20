## Param 路由参数


```ts
@Controller('/')
export class UserController {
    @Get('/:id')
    loginOptions(@Param(`id`) id: string) {}
}
```