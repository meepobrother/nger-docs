## Next函数

```ts
@Controller('/')
export class UserController {
    @Post('/login')
    login(@Next() next: (err?: Error)=>void) {}
}
```