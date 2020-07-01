# async/await

- գոյություն ունի հատուկ syntax՝ async/await կոչվող promise-ի հետ աշխատելու համար, որը հեշտ է հասկանալ և օգտագործել:

### 1. async functions

- Սկսենք async keyword-ից: Այն տեղադրվում է ֆունկցիայից առաջ։

```
async function f() {
  return 1;
}
```

- Async բառը ունի մեկ պարզ նշանակություն: Այս ֆունկցիան միշտ վերադարձնում է promise: Այլ տիպի արժեքները ավտոմատ կերպով ավարտվում են resolve եղած promise-ի նման:

```
async function f() {
  return 1;
}

f().then(res => {
    console.log(res) // 1
});
```

- Այսինքն, ֆունկցիայից առաջ async keyword-ը ապահովում է, որ այս ֆունկցիան կվերադարձնի promise:
- Կա ևս մեկ keyword` await, որը կարող է օգտագործվել միայն async ֆունկցիայի ներսում:

### 2. await

- await keyword-ը JavaScript-ի interpritator-ին ստիպելու է սպասել մինչև await-ից աջ գրված կոդը ավարտվի: Դրանից հետո այն կվերադարձնի իր արդյունքը, և կոդերի կատարումը կշարունակվի:

```
async function f() {

  let promise = new Promise((resolve, reject) => {
    setTimeout(() => resolve("ready!"), 1000)
  });

  let result = await promise;

  console.log(result);
}

f();
```

### 3. error handler

- Երբ promise-ը resolve է լինում, await promise-ը վերադարձնում է արդյունքը: Երբ դա reject լինի, error է տալու: throw Error

```
async function f() {
  await Promise.reject(new Error("Упс!"));
}
```

- Բայց կա տարբերություն, գործնականում promise-ը կարող է reject լինել ոչ թե անմիջապես, այլ որոշ ժամանակ անց: Այս դեպքում այն կհետաձգվի, և այնուհետև await-ը error կնետի:
- Նման error-ները հնարավոր է բռնել try..catch-ով:

```
async function f() {

  try {
    let response = await fetch('http://no-such-url');
  } catch(err) {
    alert(err); // TypeError: failed to fetch
  }
}

f();
```
