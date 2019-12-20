## DuplexMethod Grpc双工流


```ts
@Controller()
export class UserController {
    @DuplexMethod()
    loginOptions(input: Observable<any>): Observable<any> {}
}
```