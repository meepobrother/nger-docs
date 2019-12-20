## Info 信息

```ts
@Controller()
export class UserController {
    @Mutation()
    loginOptions(@Info() info: any): any {}
}
```