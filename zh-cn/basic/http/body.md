## Body 
> Post请求Body参数


```ts
@Controller('/')
export class UserController {
    @Post('/login')
    login(@Body(`username`) username: string) {}
}
```