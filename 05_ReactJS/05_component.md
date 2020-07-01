# ինչ է component-ը

- Կոմպոնենտները թույլ են տալիս մասնատել UI-ը միմյանցից անկախ, բազմակի օգտագործման ենթակա կտորների և մտածել ամեն կտորի մասին առանձին։
- այն ֆունկցիա է կամ class, որը վերադարձնում է JSX
- գրվում են մեծատառով
- React-ը փոքրատառով սկսվող կոմպոնենտներին դիտարկում է որպես DOM թեգեր։ Օրինակ, <div />-ը իրենից ներկայացնում է HTML-ի div թեգը, իսկ <MyDiv />-ը արդեն կոմպոնենտ է, որը պետք է լինի տեսանելիության տիրույթում։
- կանչվում են ֆունկցիայից մի քիչ տարբերվող syntax-ով
- expression, declaration, class

```
function Welcome(props) {
  return <h1>hello, {props.name}</h1>;
}

const Welcome = (props) => {
  return <h1>hello, {props.name}</h1>;
}

class Welcome extends React.Component {
  render() {
    return <h1>hello, {this.props.name}</h1>;
  }
}

<Welcome name="Jeff" />

```

- render-ը մեր component-ը DOM-ի փոխելու գործընթացն է, որը մեր browser-ը կարող է հասկանալ և ցուցադրել էկրանին:

- component-ը կարող է լինել reusable, ինչպես ֆունկցիան
