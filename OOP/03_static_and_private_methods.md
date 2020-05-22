# Static methods and properties

- Մենք կարող ենք նաև մեթոդ տալ կոնկրետ class-ին, այլ ոչ թե դրա «prototype»-ին: Նման մեթոդները կոչվում են static:

```
class User {
  static staticMethod() {
    alert(this === User);
  }
}

User.staticMethod(); // true
```

- this-ի արժեքը User.staticMethod()-ին կանչելիս հանդիսանում է user class-ի constructor-ը («օբյեկտը կետից առաջ» կանոնը):

# private methods and properties

- OOP-ում կարևոր սկզբունքներից մեկը ներքին և արտաքին ինտերֆեյսի տարանջատումն է:
  - ներքին ինտերֆեյս - երբ class-ի մեթոդները հասանելի են միայն class-ի մեջ:
  - Արտաքին ինտերֆեյս - class-ից դուրս առկա մեթոդներն ու հատկությունները:

```
class CoffeeMachine {
  #waterLimit = 200;

  #checkWater(value) {
    if (value < 0) throw new Error("Negative water");
    if (value > this.#waterLimit) throw new Error("Too much water");
  }

}

let coffeeMachine = new CoffeeMachine();

// can't access privates from outside of the class
coffeeMachine.#checkWater(); // Error
coffeeMachine.#waterLimit = 1000; // Error
```

- չի թույլատրվում փոխել/կանչել prop/մեթոդ

---

```
class CoffeeMachine {
  _waterLimit = 200;

  _checkWater(value) {
    if (value < 0) throw new Error("Negative water");
    if (value > this.#waterLimit) throw new Error("Too much water");
  }

}

let coffeeMachine = new CoffeeMachine();

coffeeMachine._checkWater();
coffeeMachine._waterLimit = 1000;
```

- թույլատրվում է փոխել/կանչել prop/մեթոդ, բայց խորհուրդ չի տրվում

---
