## @nger/rx-store

<p>
    <a href="https://www.npmjs.com/package/@nger/rx-store">
        <img src="https://img.shields.io/npm/v/@nger/rx-store.svg" alt="Version">
    </a>
    <a href="https://www.npmjs.com/package/@nger/rx-store">
        <img src="https://img.shields.io/npm/l/@nger/rx-store.svg" alt="License">
    </a>
    <a href="https://npmcharts.com/compare/@nger/rx-store?minimal=true">
        <img src="https://img.shields.io/npm/dm/@nger/rx-store.svg" alt="Downloads">
    </a>
</p>

### demo

```ts
import { StoreModule, Reducer, Store, createAction, Case, props } from '@nger/store';
import { Module, corePlatform, Injector, Injectable } from '@nger/core';
import { SomeService } from './some.service';
// state
@Injectable({
    providedIn: 'root'
})
export class DemoStore {
    title: string = `demo store`
}
// action
const updateTitle = createAction(`updateTitle`, props<{ title: string }>());
// reducer
@Reducer({
    name: `demo`,
    store: DemoStore
})
export class DemoReducer {
    constructor(private injector: Injector) { }
    @Case(updateTitle)
    updateTitle(store: DemoStore, action: { title: string }) {
        return {
            ...store,
            title: action.title
        }
    }
}
// module
@Module({
    imports: [
        StoreModule.forRoot()
    ],
    providers: [
        SomeService
    ],
    reducers: [
        DemoReducer
    ]
})
export class AppModule {
    constructor(public injector: Injector) { }
}
const platform = corePlatform();
platform.bootstrapModule(AppModule).then(res => {
    const store = res.get(Store)
    store.subscribe(res => {
        console.log(res)
    })
    store.dispatch(updateTitle({ title: 'my first title' }))
    store.dispatch(updateTitle({ title: 'my first title2' }))
    store.dispatch(updateTitle({ title: 'my first title3' }))
});
```