Create component 'word' with angular CLI
```
- $ ng generate component word
- $ ng g c word
```

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

**app.component.html**

```
<app-word></app-word>
```
