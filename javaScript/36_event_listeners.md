# addEventListener('event', callback)

```
function modifyText(new_text) {
  var t2 = document.getElementById("t2");
  t2.innerHTML = new_text;
}

const elem = document.getElementById("elem");
elem.addEventListener("click", (event) => { modifyText("four") }, false) // 1
// elem.onclick = (event) => { modifyText("four") } // 2
```

- 1-ի և 2-ի տարբերույունը այն է, որ 1-ինի դեպքում կարող ենք օգտագործել մի քանի listener, իսկ 2-ը միշտ rewrite է լինում:

# listeners

- keyup - onkeyup
- keydown - onkeydown
- onclick - click
- onmouseover - mouseover
- onmousedown - mousedown
