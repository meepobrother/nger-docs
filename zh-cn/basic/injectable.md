## Injectable
> 标注一个可自动注入的对象

```ts
export interface InjectableOptions {
    providedIn?: Type<any> | 'root' | 'platform' | 'any' | null | string;
    factory?: Function;
    deps?: any[];
}
```

### providedIn
> 注入到指定作用域 `root` 根作用域 `platform` 平台作用域 `any` 任意作用域

### factory
> 工厂方法

### deps
> 指明依赖的服务


```ts
@Injectable({
    provide: 'root'
})
export class UserService{
    getUser(id: number){
        return this.db.get({uid: id})
    }
}
```