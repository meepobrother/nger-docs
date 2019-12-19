## @nger/di

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

> 实现 `依赖注入`, from `angular`

package size:  `10.2 kB`
unpacked size: `40.6 kB`

## static create
```ts
Injector.create([])
```

## scope
> injector 作用域
```ts
import { Injector } from '@nger/di';
// scope = null
const nullInjector = Injector.create([])
// scope = root , parent scope = null
const injector = nullInjector.create([{provide: INJECTOR_SCOPE, useValue: 'root'}])
// scope = platform , parent scope = root , parent parent scope = null
const injector = injector.create([{provide: INJECTOR_SCOPE, useValue: 'platform'}])
```