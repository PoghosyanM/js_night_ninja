# Fetch

- JavaScript-ը կարող է request ուղարկել սերվերին և անհրաժեշտության դեպքում ստանալ նոր տեղեկություններ:
- fetch() մեթոդը ժամանակակից է և շատ հզոր: Այն չի սպասարկվում հին browser-ների կողմից, բայց այն սպասարկվում է բոլոր ժամանակակից browser-ների կողմից։

```
let promise = fetch(url, [options])
```

- url - հարցումը ուղարկելու URL-ը:
- options - լրացուցիչ պարամետրեր, մեթոդը, վերնագրերը և այլն:
- Առանց options, սա պարզ GET հարցումն է:
- browser-ը անմիջապես սկսում է հարցումը և վերադարձնում է promise:
- ստանալու գործընթացը սովորաբար տեղի է ունենում երկու փուլով:
- Նախ, արդյունքում ստացնում ենք ներկառուցված Response օբյեկտ, հենց որ սերվերը ուղարկում է պատասխանների վերնագրերը:
  - response-ում մենք կարող ենք տեսնել HTTP-ststus-ը:
    - ststus - HTTP հարցման ststus-ի կոդ, օրինակ, 200:
    - ok - boolean. true է, եթե HTTP ststus-ը գտնվում է 200-299 միջակայքում:
- Երկրորդ, պատասխան body-ն ստանալու համար անհրաժեշտ է օգտագործել լրացուցիչ մեթոդ:
  - Պատասխանը տրամադրում է promise-ի վրա հիմնված մի քանի մեթոդներ։
    - result.json() - վերծանում է պատասխանը JSON ձևաչափով:

```
fetch('https://randomuser.me/api/?results=10')
  .then(response => response.json())
  .then(res => console.log(res))
```

```
let response = await fetch('https://randomuser.me/api/?results=10');
let result = await response.json();
```
