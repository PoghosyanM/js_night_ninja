## Map and Set

### 1. Map

- Map - key/value հավաքածու է, ճիշտ այնպես, ինչպես օբյեկտը: Բայց հիմնական տարբերությունն այն է, որ Map-ը թույլ է տալիս օգտագործել ցանկացած տեսակի key:
- Map-ը կարող է օգտագործել object որպես key
- object-ը որպես key օգտագործելը Map-ի հայտնի և հաճախ օգտագործվող առանձնահատկություններից մեկն է: 

### 2. methods

- new Map() - ստեղծում է collection:
- map.set(key,value) - ավելացնում է property:
- map.get(key) - արժեքը վերադարձնում է ըստ key-ի կամ undefined, եթե key-ը բացակայում է:
- map.has(key) - true է դառնում, եթե key-ը առկա է collection-ի մեջ, հակառակ դեպքում false:
- map.delete(key) - տարրը ջնջում է key-ով:
- map.clear() - մաքրում է ամբողջ collection-ը:
- map.size - վերադարձնում է տարրերի քանակը:

### 3. համեմատում object-ի հետ

```
    let john = { name: "John" };
    let mapObj = new Map();
    mapObj.set(john, 'hello');
    console.log(mapObj.get(john));
```

```
    let john = { name: "John" };
    let obj = {}; 
    obj[john] = 'hello';
    console.log( obj["[object Object]"] );
```

- Map object-ը կարող է որպես key ընդունել նաև NaN
- object-ի դեպքում NaN-ը convert կլինի և կդառնա string "NaN", իսկ map-ի դեպքում ոչ
- Map.set-ի յուրաքանչյուր կանչ վերադարձնում է map օբյեկտը, որպեսզի կարողանանք նորից կանչել set մեթոդը

```
    map.set("1", "str1")
    .set(1, "num1")
    .set(true, "bool1");
```

- map-ի մեջ '1' և 1 -ը տարբեր են

### 4. loop map-ի վրա

- map-ի վրա ցիկլի համար կան 3 մեթոդներ։
    - map.keys() - վերադարձնում է key-երից կազմված array
    - map.values() - վերադարձնում է value-ներից կազմված array
    - map.entries() - վերադարձնում է key-երից և value-ներից կազմված array

```
    for (let key of map.keys()) {
        console.log(key);
    }
```

### 5. Set

- A Set-ը հատուկ տիպի value-ների collection է `առանց key-ի, որտեղ յուրաքանչյուր արժեք կարող է հանդիպել միայն մեկ անգամ:

### 6. methods

- new Set() - ստեղծում է collection, և եթե տրվում է iterable օբյեկտ (սովորաբար array), դրանց արժեքները copy է անում set-ում:
- set.add(value) - ավելացնում է value,վերադարձնում է set-ը:
- set.delete(value) – ջնջում է value
- set.has(value) - ստուգում է value-ն կա թե ոչ
- set.clear() - ջնջում է collection-ը
- set.size - տարրերի քանակն է:

՝՝՝
    let set = new Set();

    let john = { name: "John" };
    let pete = { name: "Pete" };
    let mary = { name: "Mary" };

    set.add(john);
    set.add(pete);
    set.add(mary);
    set.add(john);
    set.add(mary);

    for (let user of set) {
        console.log(user.name);
    }
՝՝՝

### 4. loop set-ի վրա

- set-ի վրա ցիկլի համար կան 3 մեթոդներ։
    - set.keys() - վերադարձնում է value-ներից կազմված iterable object
    - set.values() - նույն set.keys()-ի գործողությունը
    - set.entries() - վերադարձնում է [value, value] տեսքով iterable object