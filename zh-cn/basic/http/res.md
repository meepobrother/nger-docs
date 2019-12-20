## Response 响应

```ts
@Controller('/')
export class UserController {
    @Get('/:id')
    loginOptions(@Req() req: Request,@Res() res: Response) {}
}
```