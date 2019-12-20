## StreamMethod Stream输入常规输出


```ts
@Controller()
export class UserController {
    @GrpcMethod()
    loginOptions(input: Observable<any>): any{}
}
```