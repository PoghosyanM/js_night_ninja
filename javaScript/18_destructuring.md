## Destructuring

### 1. Destructuring-ը հատուկ sintax է, որը թույլ է տալիս մեզ «բացել» array-ը կամ object-ը մի շարք փոփոխականների մեջ, քանի որ երբեմն դա ավելի հարմար է: Destructuring-ը նույնպես հիանալի է գործում բարդ function-ների համար, որոնք ունեն շատ պարամետրեր, default value-ներ և այլն: 

### 2. Destructuring-ը array-ների համար

```
let arr = ["John", "Smith"];
let [firstName, surname] = arr;
```

```
let [first, , thirth] = [1,2,3,4,5];
console.log(second);
```

```
let [a, b, c] = "abc";
```

```
let [firstName, surname] = [];

console.log(firstName); // undefined
console.log(surname); // undefined
```

### 3. Destructuring-ը object-ների համար

- Մենք ունենք աջ կողմում object, որը մենք ուզում ենք բաժանել փոփոխականների: Ձախ կողմը պարունակում է «օրինակ» համապատասխան property-ների համար: 

``` 
    let options = {
        width: 100,
        height: 200,
    };

    let {width, height} = options;

    console.log(width);  // 100
    console.log(height); // 200
```

- Եթե ​​մենք ուզում ենք օբյեկտի prop-ը նշանակել այլ անվանում ունեցող փոփոխականի՝  «ինչ։ Որտեղ է գնում»:

```
    let {width: w, height: h} = options;
```
- default value

```
    let {width = 100, height = 200} = options;
    let {width: w = 100, height: h = 200} = options;
```

```
    let options = {
        size: {
            width: 100,
            height: 200
        },
        items: ["first", "second"],
    };

    let {
    size: {  
        width,
        height
    },
    items: [item1, item2], 
    } = options;
```