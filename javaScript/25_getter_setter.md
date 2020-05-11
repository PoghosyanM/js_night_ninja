# getter/setter

- «getter»-ը՝ կարդալու համար և «setter»-ը գրելու: Բառացիորեն հայտարարելու ժամանակ նշվում է ՝ get և set.
- get-ը ֆունկցիա է `առանց argument-ների, որը կաշխատի prwp կարդալիս
- set - ֆունկցիա, որն ընդունում է մեկ argument, որը կանճվում է prop-ը նշանակելու ժամանակ

```
let obj = {
  get propName() {
    // геттер, срабатывает при чтении obj.propName
  },

  set propName(value) {
    // сеттер, срабатывает при записи obj.propName = value
  }
};
```

- չենք կարող օգտագործել setter առանց getter-ի

```
let user = {
  name: "John",
  surname: "Smith",

  get fullName() {
    return `${this.name} ${this.surname}`;
  }
};

user.fullName; // John Smith
user.fullName = "Тест"; // Error (ունի միայն getter)
```
