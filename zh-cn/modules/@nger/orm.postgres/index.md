## @nger/orm.postgres

<p>
    <a href="https://www.npmjs.com/package/@nger/orm.postgres">
        <img src="https://img.shields.io/npm/v/@nger/orm.postgres.svg" alt="Version">
    </a>
    <a href="https://www.npmjs.com/package/@nger/orm.postgres">
        <img src="https://img.shields.io/npm/l/@nger/orm.postgres.svg" alt="License">
    </a>
    <a href="https://npmcharts.com/compare/@nger/orm.core?minimal=true">
        <img src="https://img.shields.io/npm/dm/@nger/orm.postgres.svg" alt="Downloads">
    </a>
</p>

```ts
import { Module, OnModuleInit, Injectable, corePlatform } from '@nger/core';
import { Select } from '@nger/orm';
import { PostgresOrmModule } from '@nger/orm-postgres';
@Injectable()
export class DemoInjectable {
    @Select(`select * from member`)
    getAllMembers: () => Promise<any[]>
}
@Module({
    imports: [
        PostgresOrmModule.forFeature({
            name: 'default',
            uuidExtension: 'pgcrypto',
            database: `zp`,
            entities: [],
            replication: {
                master: {
                    host: `193.112.55.191`,
                    port: 5432,
                    username: `magnus`,
                    password: `magnus`
                }
            }
        })
    ],
    controllers: [],
    providers: [
        DemoInjectable
    ]
})
export class AppModule implements OnModuleInit {
    ngOnModuleInit() {
        console.log(`AppModule`)
    }
}
const platform = corePlatform([]);
platform.bootstrapModule(AppModule).then(async res => {
    const demo = res.get(DemoInjectable)
    const allMembers = await demo.getAllMembers();
    console.log({
        allMembers
    })
})
```