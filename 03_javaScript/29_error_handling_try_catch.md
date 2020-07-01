# try..catch

- Սովորաբար script-ը անմիջապես կանգ է առնում error-ի դեպքում, որը տեսնում ենք console-ում:

### 1. Syntax

- try..catch կոնստրուկցիան բաղկացած է երկու հիմնական բլոկից: try, հետօ catch:

```
try {

  // code...

} catch (err) {

  // error handling

}
```

### 2. աշխատանքը

- Նախ, try{...} բլոկի ներսում գտնվող կոդը կատարվում է
- Եթե ​​դրա մեջ error-ներ չկան, ապա catch(err) բլոկը անտեսվում է:
- Եթե ​​դրա մեջ error է առաջացել, ապա try-ի կատարումը ընդհատվում է, և անցնում է catch(err)-ի սկզբին: err փոփոխականը (ցանկացած անուն կարող է օգտագործվել) պարունակում է error-ի օբյեկտը` տեղի ունեցածի վերաբերյալ մանրամասն տեղեկություններով:

```
try {

  alert('start');

  lalala; // error

  alert('end');

} catch(err) {

  alert('error');

}
```

### 3. try..catch-ը աշխատում է սինխրոն

- error-ը, որը տեղի է ունենալու «ապագայում», օրինակ՝ setTimeout-ում, try..catch-ը չի ​​բռնի այն։

```
try {
  setTimeout(function() {
    noSuchVariable; // error
  }, 1000);
} catch (e) {
  console.log( "don't working" );
}
```

- Դա այն է, որ ֆունկցիան կատարվում է ավելի ուշ, երբ շարժիչը արդեն դուրս է եկել try..catch-ից:

### 4. object Error

- Երբ error է առաջացել, JavaScript-ը գեներացնում է error-ի մանրամասները պարունակող օբյեկտ: Այս օբյեկտը այնուհետև որպես argument է փոխանցվում catch-ին։
  - name - error-ի անունը: Օրինակ՝ չհայտարարված փոփոխականի համար սա «ReferenceError» է:
  - message - error-ի մասին տեղեկություն տեքստի տեսքով։
  - stack - կոնկրետ stack-ը որտեղ տեղի է ունեցել։ տողը, դիրքը

### 5. throw operator

- throw operator-ը error է առաջացնում:
- throw <error object>
- JavaScript-ը ունի ներկառուցված շատ կոնստրուկտորներ՝ ստանդարտ error-ների համար։ Error, SyntaxError, ReferenceError, TypeError և այլն:

```
let json = '{ "age": 30 }';

try {

  let user = JSON.parse(json);

  if (!user.name) {
    throw new SyntaxError("Wrong data"); // (*)
  }

  alert( user.name );

} catch(e) {
  alert( "JSON Error: " + e.message ); // JSON Error: Wrong data
}
```

### 6. try…catch…finally

- try..catch կոնստրուկցիան կարող է պարունակել մեկ այլ հատված՝ finally:
- Եթե ​​կա finally, ապա այն ցանկացած դեպքում կատարվում է:

```
try {
  console.log( 'try' );
  throw "some error"
} catch (e) {
  console.log( 'catch' );
} finally {
  console.log( 'finally' );
}
```

### 7. try..catch..finally-ի փոփոխականները local են

```
try {
  let num = 1;
} catch (e) {
  console.log(e.name); // JSON Error: Wrong data
} finally {
  console.log(num); // error
}
```

### 8. try..finally

```
function func() {
  // code
  try {
    // ...
  } finally {
    // կատարվում է նաև եթե error լինի
  }
}
```

- Վերը նշված կոդով error-ը միշտ դուրս է գալիս, քանի որ catch բլոկ չկա: Բայց, finally-ն կատարվում է նախքան շարժիչը դուրս կգա բլոկից:
