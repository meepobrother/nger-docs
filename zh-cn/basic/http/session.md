## Session

```ts
@Controller('/')
export class UserController {
    @Get('/:id')
    loginOptions(@Session(`token`) token: string) {}
}
```