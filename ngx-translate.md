
**Angular version: 5.2.9**

**ngx-translate: 9.1.1**

- Install 
```
npm install @ngx-translate/core@^9.1.1 --save
npm install @ngx-translate/http-loader --save
```
<hr>

**app.module.ts**
```
import { HttpClient, HttpClientModule } from "@angular/common/http";
import { TranslateModule, TranslateLoader } from '@ngx-translate/core';
import { TranslateHttpLoader } from '@ngx-translate/http-loader';
```
```
@NgModule({
  ...
  imports: [
    ...
    HttpClientModule,
    TranslateModule.forRoot({
      loader: {
          provide: TranslateLoader,
          useFactory: (HttpLoaderFactory),
          deps: [HttpClient]
      }
    })
  ]
})
```
```
export function HttpLoaderFactory(http: HttpClient) {
  return new TranslateHttpLoader(http, './assets/i18n/', '.json');
}
```
**app.component.ts**
```
import { TranslateService } from '@ngx-translate/core';
```
```
constructor(private translate: TranslateService, ...) {
  ...
  });
  this.initTranslate();
}
```
```
initTranslate() {
  this.translate.setDefaultLang('en');

  if (this.translate.getBrowserLang() !== undefined) {
      this.translate.use(this.translate.getBrowserLang());
  } else {
      this.translate.use('en'); // Set your language here
  }
}
```
**in each page. ex home page**
**home.ts**
```
import {TranslateService} from '@ngx-translate/core';
```
```
export class HomePage {
  constructor(private translate: TranslateService, ...) {
  }
  public changeLanguage(language) {
    this.translate.use(language);
  }
}
```
**home.html**
```
<ion-header>
    <ion-navbar>
        <ion-title>
            {{ "HELLO" | translate }}
        </ion-title>
    </ion-navbar>
</ion-header>

<ion-content padding>
    <button ion-button (click)="changeLanguage('vn')">{{ 'VN' | translate }}</button>
    <button ion-button (click)="changeLanguage('en')">{{ 'ENGLISH' | translate }}</button>
</ion-content>
```
**src/assets/i18n/en.json**
```
{
    "HELLO": "Hello",
    "ENGLISH": "English",
    "VN": "Tiếng Việt"
}
```
**src/assets/i18n/vn.json**
```
{
    "HELLO": "Xin chào",
    "ENGLISH": "English",
    "VN": "Tiếng Việt"
}
```
