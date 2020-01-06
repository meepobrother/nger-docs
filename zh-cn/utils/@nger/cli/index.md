## @nger/cli
> 一款装饰器风格的命令行库
<p>
    <a href="https://www.npmjs.com/package/@nger/cli">
        <img src="https://img.shields.io/npm/v/@nger/cli.svg" alt="Version">
    </a>
    <a href="https://www.npmjs.com/package/@nger/cli">
        <img src="https://img.shields.io/npm/l/@nger/cli.svg" alt="License">
    </a>
    <a href="https://npmcharts.com/compare/@nger/cli?minimal=true">
        <img src="https://img.shields.io/npm/dm/@nger/cli.svg" alt="Downloads">
    </a>
</p>


### 定义Command

```ts
import { Command, Option, Action } from '@nger/cli';
@Command({
    name: 'demo'
})
export class DemoCommand{

    @Option()
    output: string;

    @Action()
    run(){
        console.log(`demo command run`)
    }
}
```

## 定义Module
```ts
import { Module } from '@nger/core'

@Module({
    controllers: [
        DemoCommand
    ]
})
export class CliModule{}
```

## 启动
```ts
#!/usr/bin/env node
import { platformCli } from '@nger/cli';
platformCli().bootstrapModule(CliModule)
```
