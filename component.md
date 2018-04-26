EX: Create component 'word' with angular CLI

Way 1:
```
- $ ng generate component word
```
Way 2:
```
- $ ng g c word
```

***RESULT***

**word.component.ts**
```
import { Component } from '@angular/core';

@Component({
    selector: 'app-word',
    template: '<h3>This is Word Component</h3>'
})

export class WordComponent {}
```

**app.module.ts**

```
...
import { WordComponent } from './word.component';

@NgModule({
  declarations: [
    ...
    WordComponent
  ],
...
```

***IMPORT***

**app.component.html**

```
<app-word></app-word>
```
