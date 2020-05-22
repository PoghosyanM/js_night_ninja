# class inheritence

```
class Animal {

  constructor(name) {
    this.speed = 0;
    this.name = name;
  }

  run(speed) {
    this.speed = speed;
    alert(`${this.name} runs with speed ${this.speed}.`);
  }

  stop() {
    this.speed = 0;
    alert(`${this.name} stands still.`);
  }

}

class Rabbit extends Animal {
  hide() {
    alert(`${this.name} hides!`);
  }

  stop() {
    super.stop(); // call parent stop
    this.hide(); // and then hide
  }
}

let rabbit = new Rabbit("White Rabbit");

rabbit.run(5); // White Rabbit runs with speed 5.
rabbit.stop(); // White Rabbit stands still. White rabbit hides!
```

### 1. super

- super.method(...) ծնողական մեթոդ կանչելու համար է:
- super(...) ծնող constructor-ը կանչելու համար է(միայն մեր constructor-ի ներսում):
- Ժառանգող constructor-ը պետք է կանչի super(...):

```
class Animal {
  constructor(name) {
    this.speed = 0;
    this.name = name;
  }
  // ...
}

class Rabbit extends Animal {

  constructor(name, earLength) {
    this.speed = 0;
    this.name = name;
    this.earLength = earLength;
  }

  // ...
}

// Doesn't work!
let rabbit = new Rabbit("White Rabbit", 10); // Error: this is not defined.
```

- Երբ սովորական կոնստրուկտորը կատարվում է, այն ստեղծում է դատարկ օբյեկտ և այնտեղ դնում this-ը:
- Երբ run է լինում ժառանգված class-ի constructor-ը, դա այդպես չէ: Փոխարենը, նա ակնկալում է, որ ծնող class-ի constructor-ը դա անի:
- Հետևաբար, եթե մենք ստեղծում ենք մեր սեփական կոնստրուկտորը, մենք պետք է կանչենք super(), հակառակ դեպքում դրա համար օբյեկտ չի ստեղծվի և error կստանանք:
- Rabbit կոնստրուկտորն աշխատելու համար դա օգտագործելուց առաջ պետք է զանգահարել super(), որպեսզի որևէ error չլինի:

```
class Animal {

  constructor(name) {
    this.speed = 0;
    this.name = name;
  }

  // ...
}

class Rabbit extends Animal {

  constructor(name, earLength) {
    super(name);
    this.earLength = earLength;
  }
}

// now fine
let rabbit = new Rabbit("White Rabbit", 10);
alert(rabbit.name); // White Rabbit
alert(rabbit.earLength); // 10
```
