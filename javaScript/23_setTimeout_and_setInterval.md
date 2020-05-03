# setTimeout

### ինչ է և syntax

- setTimeout-ը թույլ է տալիս կանչել function՝ որոշակի ժամանակից հետո:
- let timerId = setTimeout(func, delay, arg1, ...arg-n)
- setTimeout(() => console.log('hello'), 1000);
- setTimeout(() => console.log('hello')); // 0
- SetTimeout-ի կանչը վերադարձնում է «ID», որը կարող է օգտագործվել հետագա կատարումը չեղարկելու համար:

```
   let timerId = setTimeout(...);
   clearTimeout(timerId);
```

# setInterval

### ինչ է և syntax

- setInterval-ը թույլ է տալիս պարբերաբար կանչել function-ը՝ կրկնելով զանգը որոշակի ժամանակահատվածի ընդմիջումով:
- syntax-ով չի տարբերվում setTimeout-ից
