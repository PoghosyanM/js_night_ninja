# class

- Գործնականում մենք հաճախ պետք է ստեղծենք նույն տիպի բազմաթիվ object-ներ, օրինակ՝ user կամ այլ բան:
- Ինչպես մենք արդեն գիտենք դա կարող ենք անել constructor function-ի օգնությամբ:
- Բայց ժամանակակից JavaScript-ը ունի նաև ավելի լավ «class» կոնստրուկցիա, որն ապահովում է նոր հնարավորություններ, որոնք օգտակար են OOP-ի համար:

### 1. syntax

```
class MyClass {
  constructor() { ... }
  method1() { ... }
  method2() { ... }
  method3() { ... }
  ...
}
```

- Այնուհետև օգտագործեք new MyClass() կանչը` նոր օբյեկտ ստեղծելու համար, նշված բոլոր մեթոդներով:
- Այս դեպքում constructor() մեթոդը ինքնաբերաբար կանչվում է, դրանում մենք կարող ենք initialize անել օբյեկտը:

```
class User {

  constructor(name) {
    this.name = name;
  }

  sayHi() {
    console.log(this.name);
  }

}

let user = new User("John");
user.sayHi();
```

- Երբ կանչվում է new User("John")
  - Ստեղծվում է նոր օբյեկտ:
  - կոնստրուկտորը կանչվում է տվյալ argument-ով և պահում է այն this.name-ում:

### 2. Ինչ է class-ը

- JavaScript-ում class-ը ֆունկցիա է:

```
class User {
    constructor(name) {
        this.name = name;
    }
    sayHi() {
        alert(this.name);
    }
}

alert(typeof User); // function
```

- new User օբյեկտի մեթոդը կանչելիս այն վերցվելու է prototype-ից: Այսպիսով, new User-ի օբյեկտները մուտք ունեն class-ի մեթոդներ:

### 3. difference between class and function constructor

- Ի տարբերություն սովորական ֆունկցիայի class-ի կոնստրուկտորը չի կարող կանչվել առանց new-ի:
- class-ի մեթոդները իiterable չեն: enumirable - false
  - Եվ սա լավ է, քանի որ եթե մենք անցնում ենք for..in օբյեկտի միջոցով, ապա սովորաբար մենք չենք ցանկանում ստանալ class-ի մեթոդներ:
- class-ը միշտ օգտագործում է "use strict":

### 4. class expression

```
let User = class {
  sayHi() {
    alert("Привет");
  }
};
```

### 5. getter/setter

```
class User {

  constructor(name) {
    this.name = name;
  }

  get name() {
    return this._name;
  }

  set name(value) {
    if (value.length < 4) {
      alert("name is short");
      return;
    }
    this._name = value;
  }

}

let user = new User("John");
console.log(user.name);
```
