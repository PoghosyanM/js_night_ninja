# Rest parameter

### 1. Կարող ենք կանչել function ցանկացած թվով argument-ներով, անկախ նրանից, թե ինչպես է այն սահմանվել:
```
    function sum(a, b) {
    return a + b;
    }

    console.log( sum(1, 2, 3, 4, 5) );
```
- Լրացուցիչ argument-ները error չեն առաջացնի: Բայց, հաշվելու են միայն առաջին երկուսը:
- rest parameter-ը կարող են նշվել երեք կետով ...args ։ Բառացիորեն սա նշանակում է. «Հավաքեք մնացած argument-ները և դրեք դրանք array-ի մեջ»:

# arguments

- բոլոր ֆունկցիաները ունեն array-like object, որը կոչվում է arguments
- Նախկինում լեզվով Rest parameter չկային, և function-ի բոլոր argument-ները կարելի էր ստանալ միայն arguments-ով
- Բայց նա ունի մեկ թերություն: Չնայած arguments-ը նման են array-ի, այն array չէ: Այն չի սպասարկում array method-ները, ուստի մենք չենք կարող, օրինակ, կանչել arguments.map(...)
- Array.isArray(arguments)
- arrow function-ները this չունեն: չունեն նաև arguments:

# spread parameter

- Մենք սովորեցինք, թե ինչպես կարելի է array ստանալ argument-ներից:
- Բայց երբեմն պետք է ճիշտ հակառակն անել:
- Օրինակ, Math.max: Math.max(3, 5, 1)
- Ենթադրենք, որ մենք ունենք թվերի շարք [3, 5, 1]: Ինչպես դրա համար կանչել Math.max
- Math.max(arr[0], arr[1], arr[2])// իսկ եթե շատ են ?
- Math.max(...arr) // (օպերատոր-ը բացում է array-ը)
- աշխատում է նաև string-ի համար
- [․․․str]