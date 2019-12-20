## Query

```ts
@Controller('/')
export class UserController {
    @Get('/:id')
    loginOptions(@Query(`id`) id: string) {}
}
```