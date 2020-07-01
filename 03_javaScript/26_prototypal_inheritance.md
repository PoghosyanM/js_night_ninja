# Prototype

### 1․ ինչ է prototype-ը

- Օրինակ, մենք ունենք user օբյեկտ իր հատկություններով և մեթոդներով և ուզում ենք ստեղծել admin և հյուրի օբյեկտներ ՝ որպես դրա մի փոքր փոփոխված տարբերակներ: Մենք կցանկանայինք օգտվել user օբյեկտից, ոչ թե clone անել դրա մեթոդները, այլ պարզապես դրա հիման վրա ստեղծել նոր օբյեկտ:
- prototypal inheritance լեզվական հատկություն է, որն օգնում է դրան:

### 2․ [[Prototype]]

- JavaScript-ում օբյեկտներն ունեն հատուկ թաքնված հատկություն [[Prototype]], որը կամ null է կամ հղվում մեկ այլ օբյեկտի: Այս օբյեկտը կոչվում է «Prototype».
- [[Prototype]]-ը ներքին է և թաքնված, բայց այն սահմանելու շատ եղանակներ կան:
- Դրանցից մեկը \_\_proto\_\_-ն է

```
    let animal = {
        eats: true
    };
    let rabbit = {
        jumps: true
    };

    rabbit.__proto__ = animal;
```

### 3. \_\_proto\_\_

- \_\_proto\_\_-ն նույնը չէ ինչ -ը: Սա նրա համար getter/setter է:

```
let animal = {
  eats: true,
  walk() {
    alert("Animal walk");
  }
};

let rabbit = {
  jumps: true,
  __proto__: animal
};

let longEar = {
  earLength: 10,
  __proto__: rabbit
};

longEar.walk(); // Animal walk
console.log(longEar.jumps);
```

- Միայն երկու սահմանափակում կա.
  - Հղումները չեն կարող մտնել ցիկլի մեջ: JavaScript-ը error կտա։
  - \_\_Proto\_\_-ի արժեքը կարող է լինել օբյեկտ կամ null: Այլ տեսակներն անտեսվում են:
- prototype-ը օգտագործվում է միայն կարդալու համար:
- Write/delete գործողությունները աշխատում են ուղղակիորեն օբյեկտի հետ:
- Ստորև բերված օրինակում մենք rabbit-ին ենք տալիս սեփական walk մեթոդը:

```
let animal = {
  eats: true,
  walk() {
    /* this method won't be used by rabbit */
  }
};

let rabbit = {
  __proto__: animal
};



rabbit.walk = function() {
  console.log("Rabbit! Bounce-bounce!");
};

rabbit.walk();
```

### 4. «this»

- Անկախ նրանից, թե որտեղ է գտնվում մեթոդը։ Օբյեկտի մեջ կամ դրա prototype-ում: Երբ մեթոդը կանչվում է, this-ը միշտ օբյեկտն է կետից առաջ:

```
let animal = {
  walk() {
    if (!this.isSleeping) {
      alert(`I walk`);
    }
  },
  sleep() {
    this.isSleeping = true;
  }
};

let rabbit = {
  name: "White Rabbit",
  __proto__: animal
};

rabbit.sleep();

alert(rabbit.isSleeping); // true
alert(animal.isSleeping);
```

### 5. for...in

- For..in ցիկլը անցնում է ոչ միայն իր, այլև օբյեկտի ժառանգած հատկությունների վրայով:

```
let animal = {
  eats: true
};

let rabbit = {
  jumps: true,
  __proto__: animal
};

for(let prop in rabbit) {
    console.log(prop);
}
```
