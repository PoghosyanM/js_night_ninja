# Condition

## 1. condition 'if'

- Երբեմն մենք պետք է տարբեր գործողություններ կատարենք՝ կախված պայմաններից:
- if​​(...) օպերատորը գնահատում է փակագծերում վիճակը և, եթե արդյունքը true է, ապա կատարում է բլոկի կոդերի:
- կեղծ(falsy) արժեքներ - 0, '', null, undefined, NaN
- ճիշտ արժեքներ - մնացած բոլորը
- if(2 > 1) {console.log(true)}
- let num = 4; if(num === 4) {console.log(true)}

## 2. block "else"

- Եթե ​​հայտարարությունը պարունակում է else բլոկ: Այն կատարվում է այն դեպքում, երբ պայմանը կեղծ է:
- if(2 > 4) {console.log(true)}else{console.log(false)}

## 3. block "else if"

- Երբեմն անհրաժեշտ է ստուգել պայմանի մի քանի տարբերակ: Դա անելու համար օգտագործում ենք "else if":

## 4. ternary condition '?'

- Երբեմն անհրաժեշտ է փոփոխական նշանակել՝ կախված պայմանից:
- Այսպես կոչված ternary օպերատորի «հարցական նշանը» մեզ թույլ է տալիս դա անել ավելի կարճ և պարզ եղանակով:
- a === b ? true : false
