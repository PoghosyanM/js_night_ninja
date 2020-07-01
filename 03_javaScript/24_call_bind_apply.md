# call

- func.call(context, arg1, arg2, ...argN)
- Այն կանչում է function-ը՝ օգտագործելով առաջին argument-ը որպես իր this context, և հաջորդները՝ որպես իր argument-ներ:

```
function sayHi() {
  console.log(this.name);
}

let user = {
    name: "John",
};

sayHi.call(user);
```

# apply

- call-ի և apply-ի միակ syntax-ի տարբերությունն այն է, որ call-ը ընդունում է argument-ների ցանկ, իսկ apply-ը՝ array-like:
- func.call(context, ...arguments)
- func.apply(context, arguments)

```
function wrapper() {
  return func.apply(this, arguments);
};
```

# bind

### 1. this-ի կորուստ

```
let user = {
  firstName: "John",
  sayHi() {
    console.log(`hello, ${this.firstName}!`);
  }
};

setTimeout(user.sayHi, 1000); // hello, undefined!
```

- Դա տեղի ունեցավ այն պատճառով, որ setTimeout-ը ստացավ sayHi function-ը user object-ից առանձին (սա այն դեպքն է, երբ function-ը կորցնում է context-ը): կամ՝

```
    let f = user.sayHi;
    setTimeout(f, 1000);
```

- Բրաուզերում տեղադրված setTimeout մեթոդը ունի առանձնահատկություն. Այն սահմանում է this = window `function-ը կանչելու համար: Այսպիսով, this.firstName-ի համար այն փորձում է ստանալ windows.firstName, որը գոյություն չունի: Նման այլ դեպքերում, սա սովորաբար դառնում է undefined:

### 2. ինչպես լուծել սա

let f = user.sayHi.bind(user);

### 3. Ինչպես փոխանցել argument-ներ

- let bound = func.bind(context, [arg1], [arg2], ...);
- let bound = func.bind(context);
  - bound(args)
