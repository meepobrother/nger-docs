## GrpcMethod 常规方法

```ts
@Controller()
export class UserController {
    @GrpcMethod()
    loginOptions(input: {username: string}): {username: string} {}
}
```