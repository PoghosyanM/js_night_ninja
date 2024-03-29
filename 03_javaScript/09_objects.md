# Object

## 1. ինչ է object-ը և ինչի համար է նախատեսված

- Օբեկտներն օգտագործվում են տարբեր արժեքների և ավելի բարդ հավաքածուներ պահելու համար: JavaScript-ում շատ հաճախ է օգտագործվում այն, սա լեզվի հիմունքներից մեկն է: Հետևաբար, մենք պետք է հասկանանք դրանք, նախքան այլ տեղ խորանալը:
- Օբյակը կարող է ստեղծվել օգտագործելով գանգուր ձևավոր {...}: property-ն կազմված է զույգ արժեքից- key: value, որտեղ key-ը string է (որը նաև կոչվում է property-ի անուն»), և արժեքը կարող է լինել ցանկացած տիպի:

## 2. syntax

- let obj = new Object()
- let obj = {}
- Սովորաբար օգտագործվում է {...}-ը:
- let user = { // object-ի հայտարարում
  name: "John", // key: value
  age: 30 // key: value
  };
- property-ի անունից հետո դրվում է "։", Իսկ հետո նշվում է property-ի արժեքը:
- property-ները իրարից բաժանվում են ","-ով։

## 3. object-ի հետ աշխատանքի ձևերը

- object-ից էլէմենտ ջնջելու համար օգտագործվում է "delete"-ը
- ավելացնելու կամ փոխելու համար օգտագործվում է "․"-ը
- delete obj.a
- abj.b = 1

## 4. Քառակուսի փակագծեր

- property-ի համար, որոնց անունները բաղկացած են մի քանի բառից, «կետի միջոցով» արժեքի հասանելիությունը չի գործում։
- Նման դեպքերի համար գոյություն ունի քառակուսի փակագծերի միջոցով հատկություններին հասնելու այլընտրանքային միջոց: Այս մեթոդը կաշխատի ցանկացած property-ի անվանմամբ։
- Քառակուսի փակագծերը թույլ են տալիս նաև օգտագործել այնպիսի property, որի անունը կարող է լինել արտահայտություն: Օրինակ, property-ի անունը կարող է պահվել փոփոխականում։
- let obj = { [name]: 1, [name + 'surname']: 2 }

## 5. ընդհանուր

- հաճախ մենք պետք է օգտագործենք փոփոխականները որպես նույն անուն ունեցող property-ի արժեքներ: name: name
- name:name-ի փոխարեն մենք կարող ենք գրել պարզապես name:
- Մենք կարող ենք օգտագործել միայն string և symbol որպես key: Տվյալների բոլոր մյուս տեսակները ավտոմատ կերպով կվերափոխվեն string-ի:
- հատուկ բառերը թույլատրվում են որպես property-ի անուններ:
- ցանկացած անվանում թույլատրվում է, բայց կա հատուկ գույք \_\_proto\_\_, որը ունի հատուկ պահվածք:
- "key" in object: Ստուգում է կա key-ը թե ոչ։ true/false
- Օբեկտների առանձնահատկությունն այն է, որ դուք կարող եք մուտք գործել ցանկացած property: Նույնիսկ եթե property-ն գոյություն չունի, error չի լինի: Երբ այնտեղ չկա այն property-ն, վերադարձվում է undefined: "in"-ի օգնությամբ մենք կարող ենք ստուգել նաև դա։

## 6. "for in" loop

- ցիկլ key-երի համար
- let key in obj

## 7. copy referance-ով

- object-ի և primitive-ի տարբերություններց հիմնական տարբերություններից մեկն այն է, որ դրանք պահվում և copy-են լինում «referance»-ով:
- Փոփոխականը չի պահպանում օբյեկտը ինքնին, այլ կերպ ասած, «referance» է բացում դրան:
- Երբ օբյեկտի փոփոխականը copy է Լինում, copy է լինում «referance»-ը. Օբյեկտը ինքնին copy չի լինում:

## 8. Օբյեկտի համեմատություն

- Հավասարությունը == և խիստ հավասարություն === Օպերատորները օբյեկտների համար աշխատում են նույն կերպ:
- Երկու օբյեկտ հավասար են միայն այն դեպքում, եթե այն նույն օբյեկտն է:
- obj1 > obj2-ի նման օբյեկտների կամ obj == 5-ի հետ համեմատության համար օբյեկտները վերածվում են պրիմիտիվների:

## 9. const-ով object-ներ

- const-ով հայտարարված օբյեկտը կարող է փոփոխվել:

## 10. object-ի կլոնավորում և միացում

- Ինչպես ավելի վաղ իմացանք, օբյեկտի փոփոխականը copy անելիս նույն օբյեկտի հետ մեկ այլ հղում է ստեղծվում: Բայց ի՞նչ անենք, եթե մեզ պետք է կրկնօրինակենք object-ը:
- Object.assign(user, permissions1, permissions2);
- Եթե ​​ստացող օբյեկտը արդեն ունի նույն անունով property, այն rewrite կլինի
- կլոնավորում - let clone = Object.assign({}, user)
- Մինչ այժմ մենք ենթադրել ենք, որ օգտագործողի բոլոր property-ները primitive են: Բայց property-ները կարող են referance: Ի՞նչ անել նրանց հետ:
- Դա շտկելու համար մենք պետք է ցիկլում ստուգենք`user[key] արժեքը օբյեկտ է, և եթե այո, ապա clone անենք նաև դա: Սա կոչվում է «clone deep»:
