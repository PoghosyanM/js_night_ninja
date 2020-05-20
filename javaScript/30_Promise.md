# promise

### 1. syntax

```
let promise = new Promise(function(resolve, reject) {
  // executor function
});
```

### 2. usage

- Դրա argument-ները resolve և reject՝ callback են, որոնք JavaScript-ն ինքն է տրամադրում: Մեր կոդը միայն executor-ի ներսում է:
- Երբ նա արդյունքը կստանա, նա պետք է կանչի հետևյալ callback-ներից մեկը:
  - resolve(value) - եթե գործողությունը հաջողությամբ ավարտված է, value - արդյունք:
  - reject(error) - եթե error է առաջացել, error - error-ի օբյեկտ է:
- new Promise constructor-ի կողմից վերադարձված promise օբյեկտում կա ներքին property:
  - state - սկզբում "pending", այնուհետև "fulfilled", եթե resolve է եղել, կամ "rejected" է, եթե reject է եղել:
  - result - ի սկզբանե undefined, այնուհետև արժեքը փոխվում է value` resolve(value) կամ error՝ reject(error)

<img src="https://learn.javascript.ru/article/promise-basics/promise-resolve-reject.svg" width="700"/>

- executor-ը կատարում է առաջադրանքը (մի բան, որը սովորաբար ժամանակ է պահանջում), այնուհետև resolve/reject `փոխելու համար համապատասխան state-ը:
- promise-ը` և resolved, և rejected, համարվում է «ավարտված»։
- Կարող է լինել մի բան՝ կամ result, կամ error

````
let promise = new Promise(function(resolve, reject) {
  resolve("done"); // *****

  reject(new Error("..."));
  setTimeout(() => resolve("..."));
});```
````

# then..catch.finally

### 1. then

```
promise.then(
  function(result) { /* resolve-result */ },
  function(error) { /* reject-err */ }
);
```

- .then-ի առաջին argument-ը ֆունկցիա է, որն կատարվում է, երբ promise-ը գտնվում է resolved վիճակում և ստանում է result:
- then-ի Երկրորդ argument-ը ֆունկցիա է, որը կատարվում է այն դեպքում, երբ promise-ը գտնվում է rejected վիճակում և ստանում error:

```
let promise = new Promise(function(resolve, reject) {
  setTimeout(() => resolve("done!"), 1000);
});

promise.then(
  result => console.log(result),
  error => console.log(error)
);
```

- Եթե ​​մեզ հետաքրքրում է միայն resolve-ը, ապա այդ դեպքում կարող ենք օգտագործել միայն մեկ ֆունկցիա ․then-ի argument-ում։

### 2. catch

- Եթե ​​մենք միայն ուզում ենք մշակել error-ը կարող ենք օգտագօրծել null որպես then-ի առաջին argument կամ օգտագործել catch:

```
let promise = new Promise((resolve, reject) => {
  setTimeout(() => reject(new Error("some error!")), 1000);
});

promise.catch(err => {
  console.log(err)
});
```

### 3. finally

- try..catch բլոկի նման then..catch բլոկը նույնպես ունի finally

```
new Promise((resolve, reject) => {
  setTimeout(() => resolve("result"), 2000)
})
  .finally(() => console.log("promise finished"))
  .then(result => console.log(result));
```

### 4. Ընդհանուր

- Սովորաբար, executor-ը ինչ-որ ասինխրոն բան է անում, և դրանից հետո կանչում resolve/reject որոշ ժամանակ անց: Բայց դա պարտադիր չէ, resolve/reject-ը կարելի է անմիջապես կանչել.
