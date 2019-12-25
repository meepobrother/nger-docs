## @nger/cache.file
> CacheStore 文件驱动

<p>
    <a href="https://www.npmjs.com/package/@nger/cache-file">
        <img src="https://img.shields.io/npm/v/@nger/cache-file.svg" alt="Version">
    </a>
    <a href="https://www.npmjs.com/package/@nger/cache-file">
        <img src="https://img.shields.io/npm/l/@nger/cache-file.svg" alt="License">
    </a>
    <a href="https://npmcharts.com/compare/@nger/cache-file?minimal=true">
        <img src="https://img.shields.io/npm/dm/@nger/cache-file.svg" alt="Downloads">
    </a>
</p>


## 使用案例

```ts
import { Module, corePlatform, Injectable } from '@nger/core'
import { Cache, CacheStore } from '@nger/cache'
import { CacheFileModule } from '../lib'
import { join } from 'path'
@Injectable()
export class DemoService {
    @Cache(`username`)
    username: Promise<string>;
}

@Module({
    imports: [
        CacheFileModule.forRoot(join(__dirname, '1.txt'))
    ],
    providers: [
        DemoService
    ]
})
export class AppModule { }

corePlatform().bootstrapModule(AppModule).then(async res => {
    const cache = res.get(CacheStore)
    await cache.set(`username`,'杨明明')
    const demo = res.get(DemoService)
    const username = await demo.username;
    debugger;
})
```