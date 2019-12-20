## Headers 请求头

```ts
@Controller('/')
export class UserController {
    @Post('/login')
    login(@Headers(`Author`) author: string) {}
}
```