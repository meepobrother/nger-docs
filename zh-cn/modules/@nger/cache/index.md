## @nger/core CacheStore
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

### 使用驱动

```ts
@Module({
    imports: [
        CacheRedisModule.forFeature(options)
    ]
})
export class AppModule{}
```