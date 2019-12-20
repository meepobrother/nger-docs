## Cookies 缓存

```ts
@Controller('/')
export class UserController {
    @Post('/login')
    login(@Cookies(`token`) token: string) {}
}
```