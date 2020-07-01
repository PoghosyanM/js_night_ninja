# JSON

### 1. ինչ է JSON-ը

- եթե մենք ունենք բարդ object, և մենք ցանկանում ենք այն վերափոխել և դարձնել string,որ request ուղարկենք server: 
- կարող ենք անել հետևյալ կերպ

```
    let user = {
        name: "John",
        age: 30,

        toString() {
            return `{name: "${this.name}", age: ${this.age}}`;
        }
    };

    console.log(user.toString());
```

- Իսկ ինչ անենք եթե object-ը մեծ է

### 2․ JSON.stringify

- JSON(JavaScript Object Notation) ընդհանուր format է արժեքներն ու օբյեկտները ներկայացնելու համար: Սկզբում ստեղծվել է JavaScript-ի համար, բայց շատ այլ լեզուներ ունեն նաև գրադարաններ, որոնք կարող են աշխատել դրա հետ: Այսպիսով, JSON-ը հեշտ է օգտագործել տվյալների փոխանակման համար, երբ  օգտագործում ենք JavaScript-ը, իսկ server-ը գրված է Ruby/PHP/Java կամ որևէ այլ լեզվով:
- JSON.stringify՝ օբյեկտները JSON-ի վերածելու համար է:

```
    let user = {
        name: 'John',
        age: 30,
        isWorking: false,
        courses: ['html', 'css', 'js'],
        wife: null
    };

    let json = JSON.stringify(user);
```

- JSON.stringify() մեթոդը վերցնում է object և վերափոխում այն ​​string-ի:
- JSON-ը սպասարկում է հետևյալ dataType-երը
    - object
    - array
    - null
    - number
    - string
    - boolean

```
    let user = {
        foo() {            // անտեսում է
            return 1
        },
        [Symbol("id")]: 123, // անտեսում է
        something: undefined // անտեսում է
    };

    alert( JSON.stringify(user) ); // {} (դատարկ объект) 
```

```
    let user = {
        name: 'John',
        surname: 'Smith'
    }

    JSON.stringify(user, function replacer(key, value) {
        alert(`${key}: ${value}`);
        return (key == 'name') ? undefined : value;
    }, 3)
```

### 2․ JSON.parse

- JSON.parse՝ JSON-ը օբյեկտի վերածելու համար է:
- այն ունի մի քանի օրենքներ

```
let json = `{
    name: "John",                     // Error: key-ը առանց զույգ փակագծերի է
    "surname": 'Smith',               // Error: value-ն կենտ փակագծերով է
    'isAdmin': false                  // Error: key-ը կենտ փակագծերով է
    "friends": [0,1,2,3]                     // Здесь всё в порядке
}`;
```

- JSON-ում comment-ները չեղարկվում են։