# Object convertion

## 1. simbol.toPrimitive, toString and valueOf

- simbol.toPrimitive - աշխատում է առաջինը
- toString - աշխատում է երբ hint-ը հավասար է string
- valueOf - աշխատում է երբ hint-ը հավասար է number կամ default

## 2. Hint

- default - երբ օգտագործվում է binary "+"-ը, քանի որ այն միայն գումարման համար չէ։ (obj + 1)
- string - Օբյեկտն string-ի վերափոխելու համար, երբ գործողությունն ակնկալում է string (alert)
- օբյեկտը թվի վերափոխելու համար, մաթեմատիկական գործողությունների դեպքում։ (+obj)
