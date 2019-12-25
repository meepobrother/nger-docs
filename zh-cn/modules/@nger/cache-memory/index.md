## @nger/cache-memory
> CacheStore 内存驱动

<p>
    <a href="https://www.npmjs.com/package/@nger/cache-memory">
        <img src="https://img.shields.io/npm/v/@nger/cache-memory.svg" alt="Version">
    </a>
    <a href="https://www.npmjs.com/package/@nger/cache-memory">
        <img src="https://img.shields.io/npm/l/@nger/cache-memory.svg" alt="License">
    </a>
    <a href="https://npmcharts.com/compare/@nger/cache-memory?minimal=true">
        <img src="https://img.shields.io/npm/dm/@nger/cache-memory.svg" alt="Downloads">
    </a>
</p>


## Demo

```ts
import { Module, corePlatform, Injectable } from '@nger/core'
import { Cache, CacheStore } from '@nger/cache'
import { CacheMemoryModule } from '../lib'
@Injectable()
export class DemoService {
    @Cache(`username`)
    username: Promise<string>;
}

@Module({
    imports: [
        CacheMemoryModule.forRoot({})
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