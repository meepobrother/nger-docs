## @nger/http-node
> node端相应或发送http请求,如果`http`开头会请求远程的`url`,否则请求本地`Controller`定义的响应


<p>
    <a href="https://www.npmjs.com/package/@nger/http-node">
        <img src="https://img.shields.io/npm/v/@nger/http-node.svg" alt="Version">
    </a>
    <a href="https://www.npmjs.com/package/@nger/http-node">
        <img src="https://img.shields.io/npm/l/@nger/http-node.svg" alt="License">
    </a>
    <a href="https://npmcharts.com/compare/@nger/http-node?minimal=true">
        <img src="https://img.shields.io/npm/dm/@nger/http-node.svg" alt="Downloads">
    </a>
</p>


```ts
import { HttpClient, HttpModule, Query, Get } from '@nger/http';
import { corePlatform, Module, Controller } from '@nger/core';
import { writeFileSync } from 'fs';
import { HttpNodeModule } from '@nger/http-node'
import { join } from 'path';

@Controller()
export class DemoController {
    @Get(``)
    getHome() {
        return `welcome to nger home!`
    }
    @Get(`user`)
    getUser(@Query(`id`) id: number, @Query(`name`) name: string) {
        return `welcome to user home! ${id}-${name}`
    }
}
@Module({
    imports: [
        HttpNodeModule,
        HttpModule
    ],
    providers: [],
    controllers: [DemoController]
})
export class AppModule { }
corePlatform().bootstrapModule(AppModule).then(res => {
    const client = res.get(HttpClient)
    client.get(`./user?id=2`, {
        params: {
            name: 'imeepos'
        }
    }).subscribe(res => {
        writeFileSync(join(__dirname, `index.html`), res)
        debugger
    })
})
```