# module

### 1. ինչ է մոդուլը

- Մոդուլը պարզապես ֆայլ է: Մեկ script-ը մեկ մոդուլ է:
- Մոդուլները կարող են load անել միմյանց և օգտագործել import և export հրահանգներ՝ որ օգտագործենք կամ փոխենք մեկ այլ մոդուլի ֆունկցիոնալությունը:
- export - նշում են փոփոխականներն ու գործառույթները, որոնք պետք է մատչելի լինեն գործող մոդուլից դուրս:
- import - թույլ է տալիս import անել ֆունկցիոնալությունը այլ մոդուլներից:

```
// say.js

export function sayHi(user) {
  return `Hello, ${user}!`;
}

// index.js

import {sayHi} from './say.js';

document.body.innerHTML = sayHi('John');

```

- մոդուլում միշտ միացված է "use strict"
- մոդուլում this-ը սահմանված չէ

```
<script type="module">
  a = 5; // error
</script>
```

- մոդուլները ունեն սեփական տեսանելիության տիրույթ

```
<script type="module">
  let user = "John";
</script>

<script type="module">
  alert(user); // Error: user is not defined
</script>
```

### 2. import.meta

- Import.meta օբյեկտը պարունակում է տեղեկատվություն ընթացիկ մոդուլի վերաբերյալ:
