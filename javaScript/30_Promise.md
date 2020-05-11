# promise

### 1. syntax

```
let promise = new Promise(function(resolve, reject) {
  // executor function
});
```

### 2. usage

- Դրա argument-ները resolve և reject՝ callback են, որոնք JavaScript-ն ինքն է տրամադրում: Մեր կոդը միայն executor-ի ներսում է:
- Երբ նա արդյունքը կստանա, նա պետք է կանչի հետևյալ callback-ներից մեկը:
  - resolve(value) - եթե գործողությունը հաջողությամբ ավարտված է, value - արդյունք:
  - reject(error) - եթե error է առաջացել, error - error-ի օբյեկտ է:
- new Promise constructor-ի կողմից վերադարձված promise օբյեկտում կա ներքին property:
  - state - սկզբում "pending", այնուհետև "fulfilled, եթե resolve է եղել, կամ "rejected" է, եթե reject է եղել:
  - result - ի սկզբանե undefined, այնուհետև արժեքը փոխվում է value` resolve(value) կամ error՝ reject(error)

<img src="https://learn.javascript.ru/article/promise-basics/promise-resolve-reject.svg" width="300"/>
