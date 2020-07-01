# import/export

### 1. Եղանակները

- export {f1, f2};
  - import { f1, f2 } from './index.js'
  - import \* as someName from './index.js'
- export const f1 = () => {...}
  - import { f1 } from './index.js'
  - import { f1 as someName } from './index.js'
- export default f1
  - import someName from './index.js'
- export default f1 = () => {...}
  - import someName from './index.js'

### 2. կանոններ

- Մենք կարող ենք import/export դնել script-ի սկզբում կամ վերջում, դա նշանակություն չունի:

```
sayHi();

// ...

import {sayHi} from './say.js';
```

- Գործնականում import-ներն ամենից հաճախ տեղակայված են ֆայլի սկզբում: Բայց սա միայն ավելի մեծ հարմարության համար:
- բլոկի մեջ չի աշխատում import/export - {...}

```
if (something) {
  import {sayHi} from "./say.js"; // error
}
```
