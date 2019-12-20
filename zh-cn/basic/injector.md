## Injector 依赖注入操作对象


    
### get

```ts
abstract get<T>(token: IToken<T>, notFoundValue?: T | undefined | null, flags?: InjectFlags): T;
```
> 根据`token`换服务, `notFoundValue`指定未找到的值, 
> flags注入标志: 
>   `Default` 默认，`找不到`并且`默认值`不存在报错
>   `Host` 只取当前`Controller`中注入的服务
>   `Self` `本作用域`下查找
>   `SkipSelf` 跳过`本作用域`查找
>   `Optional` 可以为空

```ts
const userService = injector.get(UserService)
```

### create
```ts
abstract create(records: StaticProvider[], source?: string | null): Injector;
```
> 创建子作用域`Injector`

```ts
const childInjector = injector.create([])
```