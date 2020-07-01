# Native prototypes

- «prototype» prop-ը լայնորեն օգտագործվում է հենց JavaScript-ի core-ից:

```
let obj = {};
console.log( obj + 1 ) // toString
```

### 1. Object.prototype

- obj = {} նույնն է, ինչ obj = new Object(), որտեղ Object-ը ներկառուցված constructor function է իր սեփական [[prototype]]-ով, ինչը հղվում է հսկայական օբյեկտին, որն ունի toString մեթոդ և այլն:

<img src="https://learn.javascript.ru/article/native-prototypes/object-prototype-1.svg" width="700"/>

- ներկառուցված բոլոր «prototype»-երի վերևում գտնվում է Object.prototype: Ահա թե ինչու են ասում, որ JS-ում «ամեն ինչ ժառանգվում է օբյեկտից»:

<img src="https://i.stack.imgur.com/d4bDt.png" width="700"/>

### 2. Primitives

- Ամենաբարդ բանը տեղի է ունենում stringi-ի, number-ի և boolean-ի հետ:
- Ինչպես հիշում ենք, դրանք օբյեկտ չեն: Բայց եթե մենք փորձենք մուտք գործել դրանց prop-ներ, ապա կստեղծվի ժամանակավոր wrapper object՝ օգտագործելով buid-in String, Number և Boolean constructor-ը, որոնք կապահովեն մեթոդներ, այնուհետև կվերանան:
- Այս օբյեկտները ստեղծվում են մեզ համար անտեսանելիորեն, և շարժիչների մեծ մասը օպտիմիզացնում է այս գործընթացը: Այս օբյեկտների մեթոդները հանդիպում են նաև prototype-ում, որոնք հասանելի են String.prototype-ի, Number.prototype-ի և Boolean.prototype-ի մեջ:

### object առանց \_\_proto\_\_

- Object.create (proto descriptors) - ստեղծում է դատարկ օբյեկտ [[prototype]] prop-ով, որը նշված է որպես \_\_proto\_\_ (կարող է լինել null):

```
let obj = Object.create(null);

alert(obj); // Error (no toString)
```

```
let animal = {
  eats: true,
};

let rabbit = Object.create(animal, {
  jumps: {
    value: true,
  },
});

console.log(rabbit); // true
```
