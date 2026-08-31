---
title: "CharacterData: previousElementSibling property"
---

---
title: "CharacterData: previousElementSibling property"
short-title: previousElementSibling
slug: Web/API/CharacterData/previousElementSibling
page-type: web-api-instance-property
browser-compat: api.CharacterData.previousElementSibling
---

{{APIRef("DOM")}}

ویژگی فقطخواندنیِ **`previousElementSibling`** در رابط {{domxref("CharacterData")}} نخستین عنصر ({{domxref("Element")}}) قبل از گرهٔ کنونی را در فهرست فرزندانِ والد برمی‌گرداند؛ اگر چنین عنصری وجود نداشته باشد، `null` برمی‌گردد.

## Value

یک شیء {{domxref("Element")}}، یا اگر عنصر همسطحی (sibling) یافت نشود، `null`.

## Example

```html
<div id="div-01">Here is div-01</div>
TEXT
<div id="div-02">Here is div-02</div>
SOME TEXT
<div id="div-03">Here is div-03</div>
<pre>Result</pre>
```

```js
// Initially set node to the Text node with `SOME TEXT`
let node = document.getElementById("div-02").nextSibling;

let result = "Previous element siblings of SOME TEXT:\n";

while (node) {
  result += `${node.nodeName}\n`;
  node = node.previousElementSibling;
}

document.querySelector("pre").textContent = result;
```

{{EmbedLiveSample("Example", "100%", "200")}}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("CharacterData.nextElementSibling")}}