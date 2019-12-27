## @nger/cookies

```ts
import {
  CookieService,
  ServerCookiesModule,
  Cookies,
  CURRENT_SECRET,
  COOKIE_SECRET
} from "@nger/cookies";
import {
  corePlatform,
  Module,
  Controller,
  HttpRequest,
  HttpHeaders
} from "@nger/core";
import { Get, HttpModule, REQUEST } from "@nger/http";
@Controller(``)
export class DemoController {
  @Get()
  add(@Cookies(`username`) username?: string) {
    console.log({ username });
  }
}

@Module({
  imports: [ServerCookiesModule.forFeature("mmp"), HttpModule],
  controllers: [DemoController]
})
export class ChildModule {}

@Module({
  imports: [ServerCookiesModule.forFeature("ymm"), ChildModule],
  providers: [
    {
      provide: REQUEST,
      useValue: new HttpRequest(`GET`,``,{},{headers: new HttpHeaders({cookie: 'username=ymm;password=123qwe'})})
    }
  ]
})
export class AppModule {}
corePlatform()
  .bootstrapModule(AppModule)
  .then(res => {
    const childRef = res.getModuleRef(ChildModule);
    if (childRef) {
      const controller = childRef.get(DemoController);
      controller.add();
      const childCookie = childRef.get(CookieService);
      const currentSecret = childRef.get(CURRENT_SECRET);
      const cookies = childCookie.serialize({
        password: `111`,
        username: `222`
      });
      debugger;
    }
    const cookie = res.get(CookieService);
    const cookiesSerialize = cookie.serialize({
      name: `111`,
      username: `222`
    });
    const obj = cookie.parse(cookiesSerialize);
    const currentSecret = res.get(CURRENT_SECRET);
    const secrets = res.get(COOKIE_SECRET);
    debugger;
  });
```