# Closure

### 1. ինչ է closure-ը

- JavaScript-ը ուժեղ ֆունկցիոնալ ուղղվածություն ունեցող լեզու է: Նա մեզ շատ ազատություն է տալիս: function-ը կարող է դինամիկ կերպով ստեղծվել, պատճենվել մեկ այլ փոփոխականի կամ փոխանցվել որպես function-ի այլ argument, իսկ ավելի ուշ կանչվել է բոլորովին այլ վայրից:
- Մենք գիտենք, որ function-ը կարող է մուտք գործել արտաքին միջավայրի փոփոխականներ, այս հատկությունը օգտագործվում է շատ հաճախ:
- Բայց ի՞նչ է պատահում, երբ արտաքին փոփոխականները փոխվում են: function-ը կստանա վերջին արժեքը, որն առկա էր գործառույթի ստեղծման պահի՞ն
- Եվ ի՞նչ է պատահում, երբ function-ը տեղափոխվում է մեկ այլ վայր և կանչվում է այնտեղից, արդյո՞ք դա հասանելիություն կստանա իր նոր գտնվելու վայրի արտաքին փոփոխականներին:

### 2․ օրինակներ

```
    let name = "John";

    function sayHi() {
        console.log("Hi, " + name);
    }

    name = "Smith";

    sayHi(); // "John" թե "Smith"?
```

```
    function makeWorker() {
        let name = "Smith";

        return function() {
            console.log(name);
        };
    }

    let name = "John";

    // create a function
    let work = makeWorker();

    // call it
    work(); // "Smith" թե "John"
```

### 3. Lexical Environment

- JavaScript-ում կատարված յուրաքանչյուր function-ի կոդ բլոկում գրություն ունի ներքին (թաքնված) օբյեկտ, որը կոչվում է Lexical Environment
- այն բաղկացած է 2 մասից
  - Environment record - օբյեկտ, որում բոլոր ներքին փոփոխականները պահվում են որպես prop-ներ(ինչպես նաև որոշ այլ տեղեկություններ, ինչպիսին է this-ը):
  - Հղում է արտաքին Lexical Environment։ Այսինքն՝ այն, որը համապատասխանում է կոդից դուրս գտնվող հատվածին ։
- «Փոփոխականը» պարզապես հատուկ ներքին օբյեկտի prop է։ Environment record: «Ստանալ կամ փոխել փոփոխական» նշանակում է ՝ «ստանալ կամ փոխել այս օբյեկտի prop-ը»:
- Ի տարբերություն let-ի միջոցով հայտարարված փոփոխականների, function declaration-ը ամբողջությամբ չեն նախաստորագրվում, երբ դրանց կատարումը հասնում է դրանց, այլ ավելի վաղ, երբ ստեղծվում է Lexical Environment-ը:

### 4. Ներքին և արտաքին Lexical Environment

```
    let hi = "Hello"

    function foo(name) {
        return  hi + name
    }

    let hi = "Barev"

    foo("John")
```

- Այսպիսով, ֆունկցիա կանչելիս մենք ունենք երկու Lexical Environment՝ ներքին և արտաքին(գլոբալ)։
  - ներքին-ը պարունակում է մեկ փոփոխական name՝ function-ի argument:
  - արտաքին-ը պարունակում է փոփոխական hi-ը և function foo-ն
- Երբ կոդը ցանկանում է մուտք գործել փոփոխական, նախ որոնումը կատարվում է ներքին Lexical Environment-ում, այնուհետև արտաքինում, ապա հաջորդում և այդպես շարունակ, մինչև գլոբալ:
- function-ը ստանում է արտաքին փոփոխականների վերջին արժեքը
- function-ի նոր Lexical Environment ստեղծվում է ամեն անգամ, երբ function-ը կկանչվի:
- Եվ, եթե մի ֆունկցիա կանչվում է մի քանի անգամ, ապա յուրաքանչյուր կանչ կունենա իր Lexical Environment-ը՝ իր սեփական ներքին փոփոխականներով և argument-ներով:

### 5. nested function

- function-ը կոչվում է «nested, երբ այն ստեղծվում է մեկ այլ function-ի ներսում:

```
    function makeCounter() {
        let count = 0;

        return function() { // nested function
            return count++;
    };
    }

    let counter = makeCounter();
    let counter2 = makeCounter();
```

- Ինչպե՞ս է դա գործում ներսից:
  - Երբ ներքին function-ը սկսում է կատարվել, սկսվում է count փոփոխականի որոնումը ներսից-դուրց:
- MakeCounter-ի յուրաքանչյուր կանչի ստեղծվում է function-ի համար նոր Lexical Environment՝ իր count-ով: Այսպիսով, արդյունքում ստացված counter function-ները անկախ են:
- ստեղծման պահին բոլոր function-ները ստանում են թաքնված prop [[Enviroment]], որը հղվում է այն Lexical Environment, որտեղ որ ինքը ստեղծվել է։
- Այս դեպքում makeCounter-ը ստեղծվում է գլոբալ Lexical Environment-ում, և [[Environment]]-ը պարունակում է դրա հղումը:

### 6. Garbage collection

- Սովորաբար, function-ի կանչից հետո Lexical Environment-ը հանվում է հիշողությունից `բոլոր փոփոխականներով: Դա այն պատճառով է, որ դրանում հղումներ չկան: Որպես JavaScript-ի ցանկացած object, այն պահվում է միայն հիշողության մեջ, մինչդեռ այն հասանելի է:
- … Բայց եթե կա nested function, որը function-ի ավարտից հետո դեռ հնարավոր է մուտք գործել, ապա այն [[Environment]] հատկություն ունի:
- Այդ դեպքում Lexical Environment-ը դեռևս հասանելի է նույնիսկ function-ի ավարտից հետո, ուստի այն է մնում:
