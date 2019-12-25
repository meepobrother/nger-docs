## @nger/rx-effects

<p>
    <a href="https://www.npmjs.com/package/@nger/rx-effects">
        <img src="https://img.shields.io/npm/v/@nger/rx-effects.svg" alt="Version">
    </a>
    <a href="https://www.npmjs.com/package/@nger/rx-effects">
        <img src="https://img.shields.io/npm/l/@nger/rx-effects.svg" alt="License">
    </a>
    <a href="https://npmcharts.com/compare/@nger/rx-effects?minimal=true">
        <img src="https://img.shields.io/npm/dm/@nger/rx-effects.svg" alt="Downloads">
    </a>
</p>


### Demo

```ts
import { StoreModule, Reducer, Store, createAction, Case, props } from '@nger/rx-store';
import { Module, corePlatform, Injector, Injectable } from '@nger/core';
import { createEffect, Actions, ofType, EffectsModule } from '../lib';
import { map, catchError, switchMap, mergeMap } from 'rxjs/operators';
import { of, EMPTY } from 'rxjs';
// state
@Injectable({
    providedIn: 'root'
})
export class DemoStore {
    title: string = `demo store`
}
// action
const updateTitle = createAction(`updateTitle`, props<{ title: string }>());
const updateSuccessTitle = createAction(`updateSuccessTitle`, props<{ title: string }>());

// reducer
@Reducer({
    name: `demo`,
    store: DemoStore
})
export class DemoReducer {
    constructor(private injector: Injector) { }
    @Case(updateSuccessTitle)
    updateTitle(store: DemoStore, action: { title: string }) {
        return {
            ...store,
            title: action.title
        }
    }
}
// service
@Injectable()
export class DemoService {
    updateTitle(title: string) {
        return of({
            title: title +' saved!!'
        })
    }
}
// effects
@Injectable()
export class DemoEffects {
    updateTitle = createEffect(() => this.actions.pipe(
        ofType(updateTitle),
        mergeMap((action) => this.demo.updateTitle(action.title).pipe(
            map(it => updateSuccessTitle(it)),
            catchError(() => EMPTY)
        ))
    ))

    constructor(private actions: Actions, private demo: DemoService) { }
}
// module
@Module({
    imports: [
        StoreModule.forRoot(),
        EffectsModule.forRoot([
            DemoEffects
        ])
    ],
    providers: [
        DemoService
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
    store.select(`demo`).subscribe(res => {
        console.log(res.title)
    })
    store.dispatch(updateTitle({ title: 'my first title' }))
});

```