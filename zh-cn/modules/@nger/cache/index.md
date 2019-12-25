## @nger/core CacheStore
<p>
    <a href="https://www.npmjs.com/package/@nger/core">
        <img src="https://img.shields.io/npm/v/@nger/core.svg" alt="Version">
    </a>
    <a href="https://www.npmjs.com/package/@nger/core">
        <img src="https://img.shields.io/npm/l/@nger/core.svg" alt="License">
    </a>
    <a href="https://npmcharts.com/compare/@nger/core?minimal=true">
        <img src="https://img.shields.io/npm/dm/@nger/core.svg" alt="Downloads">
    </a>
</p>
> 缓存接口

### set
```ts
abstract set<T>(key: string, value: T, options?: CacheStoreSetOptions<T>): Promise<void>
```
> 设置缓存

### get
```ts
abstract get<T>(key: string): Promise<T | undefined>;
```
> 获取缓存


### del
```ts
abstract del(key: string): Promise<void>;
```
> 删除缓存

### 使用
```ts
import { CacheStore } from '@nger/core';
export class DemoController{
    constructor(private store: CacheStore){}
    getUser() {
       return this.store.get('fromUser')
    }
}
```

### 存储驱动
| 名称                    | 作用                 |
| ----------------------- | -------------------- |
| [@nger/cache.file](/)   | 缓存到文件           |
| [@nger/cache.redis](/)  | 缓存到redis          |
| [@nger/cache.memory](/) | 缓存到内存           |
| [@nger/cache.pg](/)     | 缓存到postgres数据库 |

### Demo

```ts
import { Module, corePlatform, Injectable } from '@nger/core'
import { Cache, CacheModule } from '@nger/cache'

@Injectable()
export class DemoService {
    @Cache(`demo`)
    demo: Promise<{ key: string }>;
}


export class DemoCache {
    async get<T>(key: string): Promise<T | undefined> {
        return {
            key
        } as any;
    }
}


@Module({
    imports: [
        CacheModule.forRoot(DemoCache as any)
    ],
    providers: [
        DemoService
    ]
})
export class AppModule { }

corePlatform().bootstrapModule(AppModule).then(async res => {
    const demo = res.get(DemoService)
    const demo2 = await demo.demo;
    debugger;
})
```