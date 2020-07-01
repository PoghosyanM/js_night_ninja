# getter/setter

- «getter»-ը՝ կարդալու համար և «setter»-ը գրելու: Բառացիորեն հայտարարելու ժամանակ նշվում է ՝ get և set.
- get-ը ֆունկցիա է `առանց argument-ների, որը կաշխատի prop կարդալիս
- set - ֆունկցիա, որն ընդունում է մեկ argument, որը կանչվում է prop-ը նշանակելու ժամանակ

```
let obj = {
  get propName() {
    // կարդալու համար
  },

  set propName(value) {
    // գրելու համար - obj.propName = value
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
user.fullName = "Test"; // Error (ունի միայն getter)
```
