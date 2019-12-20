## Inject
> 取指定`token`的注入服务,内部执行了`injector.get(token)`

```ts
export interface InjectOptions {
    token: any;
}
```

```ts
controller(@Inject(UserToken) private user: UserInfo){}
```
