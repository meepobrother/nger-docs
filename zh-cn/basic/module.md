## Module 模块
> 一个模块由一些`子模块`,`控制层`,`服务层`组合而成.

```ts
export const ModuleMetadataKey = `ModuleMetadataKey`;
export interface ModuleOptions {
    id?: string; // module id
    providers?: (Provider[] | Provider)[]; // 服务注册
    imports?: Array<Type<any> | ModuleWithProviders<any>>; // 依赖模块
    exports?: Array<any>; // 导出服务
    controllers?: (Provider[] | Provider)[];// 控制器
}
export const Module = createClassDecorator<ModuleOptions>(ModuleMetadataKey);
export const NgModule = Module;
```

### exports导出
1. 将当前模块的某些服务导出以供其他模块使用。导出后会注入到根`Module`

### controllers与providers的区别
1. `controllers`与`providers`都可以用来`注入服务`,不同的是providers在当前作用域(`injector`)内是单例。
2. `controllers`每次获取都会重新创建,`controllers`一搬用于处理用户请求。
3. 当用户请求完成时调用`注销钩子`注销资源。
4. 创建完成后调用`初始化钩子`初始化一些资源。

### 注意
`controllers`里可以是任意`Provider`,与装饰器`@Controller`并无关联。
`@Controller`装饰的类注入到`controllers`后会自动注入到根`Module`。