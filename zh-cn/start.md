## 起步

1. 准备`AppModule`

```ts
import { Module } from '@nger/core';
@Module()
export class AppModule{}
```

2. 启动

```ts
import { corePlatform } from '@nger/core';
corePlatform().bootstrapModule(AppModule)
```

