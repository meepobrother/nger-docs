## Ip 获取Ip地址

```ts
@Controller('/')
export class UserController {
    @Post('/login')
    login(@Ip() ip: string) {}
}
```