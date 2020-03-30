## 1. number

- 1, 1.5
- NaN - 'name' / 2
- infinity - 1 / 0
- մաթ․ գործողություններ - \* / - +

## 2. bigint

- 2-53 աստճանից բարձր JS-ը սխալ է կատարում մաթ․ գործ-երը
- bigint - 999999999999999999999999999999999999n

## 3. string

- 'name'
- "name"
- `hello ${name}`

## 4. boolean

- true 2 > 1
- false 2 < 1>

## 5. null

- null

## 6. undefined

- undefined - let name;

## 7. symbol

- symbol տեսակը օգտագործվում է օբյեկտների համար ունիկալ id ստեղծելու համար:

## 8. object

- object տիպը հատուկ է:
- Մնացած բոլոր տիպերը կոչվում են primitive, քանի որ դրանց արժեքները կարող են լինել միայն պարզ արժեքներ (լինի դա string կամ number, կամ որևէ այլ բան): Օբեկտներն օգտագործվում են տվյալների կամ ավելի բարդ օբյեկտների հավաքածուներ պահելու համար:

## 9. typeof

- Typeof օպերատորը վերադարձնում է տեսակը: Սա օգտակար է այն դեպքում, երբ մենք ուզում ենք տարբեր ձևերով կարգավորել տարբեր տիպի արժեքները, կամ պարզապես ուզում ենք ստուգում անել:
- typeof(name)
- typeof name
- վերադարձնում է տիպը string-ի տեսքով
- typeof undefined - "undefined"
- typeof 0 - "number"
- typeof 10n - "bigint"
- typeof true - "boolean"
- typeof "John" - "string"
- typeof Symbol("id") - "symbol"
- typeof null - "object"
