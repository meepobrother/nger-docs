## Context

```ts
@Controller()
export class UserController {
    @Mutation()
    loginOptions(@Context() context: any): any {}
}
```