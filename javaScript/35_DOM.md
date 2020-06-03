# DOM - Document Object Model

## getElement*, querySelector*

### 1. document.getElementById/getElementsclassName

- Id-ի արժեքը պետք է լինի եզակի: file-ում տվյալ ID-ի հետ կարող է լինել միայն մեկ տարր: Եթե file-ը ունի նույն id արժեք ունեցող մի քանի տարր, ապա այն կընտրվի պատահական սկզբունքով: browser-ը կարող է պատահականորեն վերադարձնել դրանցից որևէ մեկը: Հետևաբար, պետք է պահպանել եզակի id-ի պահպանման կանոնը:

```
<div id="elem">
  <div id="elem">Element</div>
  <p class="paragraf">paragraf1<p/>
  <p class="paragraf">paragraf2<p/>
</div>

<script>
  let elem = document.getElementById('elem')
  let p = document.getElementsclassName('paragraf')
  elem.innerHTML = 'another element'
  elem.style.background = 'red';
</script>
```

### 2. querySelectorAll(css)

- search-ի ամենատարածված մեթոդը elem.querySelectorAll(css)-ն է, այն վերադարձնում է elem-ի բոլոր տարրերը, որոնք բավարարում են CSS-ի այս selector-ին:

```
<ul>
  <li>this</li>
  <li>test</li>
</ul>
<ul>
  <li>finished</li>
  <li>successfully</li>
</ul>
<script>
  let elements = document.querySelectorAll('ul > li:last-child');

  for (let elem of elements) {
    alert(elem.innerHTML);
  }
</script>
```

### 3. querySelector(css)

- elem.querySelector(css) մեթոդը վերադարձնում է առաջին տարրը, որը համապատասխանում է տվյալ CSS selector-ին:

### 4. getElementsByTagName(div or \*)

```
<table id="table">
  <tr>
    <td>age:</td>

    <td>
      <label>
        <input type="radio" name="age" value="young" checked> 18 years
      </label>
      <label>
        <input type="radio" name="age" value="mature"> 18 from 50
      </label>
      <label>
        <input type="radio" name="age" value="senior"> 60 and old
      </label>
    </td>
  </tr>
</table>

<script>
  let inputs = table.getElementsByTagName('input');

  for (let input of inputs) {
    alert( input.value + ': ' + input.checked );
  }
</script>
```

### 5. class and style

- class

  - classList.add('name', 'name2') - ավելացնում է class
  - classList.remove('name', 'name2') - ջնջում է class-ը
  - classList.contains('name') - ստուգում է կա թե ոչ true/false

- style

  - elem.style.cssText = "color: blue; border: 1px solid black";
  - elem.style.color = "blue";

### 6. Ընդհանուր

- setAttribute
- innerHTML
- innerText
- append
- prepend
- before
- after

<img src="https://learn.javascript.ru/article/modifying-document/before-prepend-append-after.svg" width="700"/>
