## MethodStream 常规输入Stream输出

```ts
@Controller()
export class UserController {
    @GrpcMethod()
    loginOptions(input: any): Observable<any>{}
}
```