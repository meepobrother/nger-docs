## Source


```ts
@Controller()
export class UserController {
    @Mutation()
    loginOptions(@Source() source: any): any {}
}
```