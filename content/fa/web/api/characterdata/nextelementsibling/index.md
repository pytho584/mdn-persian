---
title: "CharacterData: nextElementSibling property"
short-title: nextElementSibling
slug: Web/API/CharacterData/nextElementSibling
page-type: web-api-instance-property
browser-compat: api.CharacterData.nextElementSibling
---

{{APIRef("DOM")}}

ویژگی فقط‌خواندنی **`nextElementSibling`** در رابط {{domxref("CharacterData")}}، نخستین گرهٔ {{domxref("Element")}} را پس از گرهٔ مشخص‌شده در فهرست فرزندان والد همان گره برمی‌گرداند. اگر عنصر مشخص‌شده آخرین عنصر در آن فهرست باشد، مقدار `null` برگردانده می‌شود.

## Value

یک شیء {{domxref("Element")}}، یا اگر همشاخه‌ای (sibling) یافت نشود، `null`.

## Example

```html
TEXT
<div id="div-01">Here is div-01</div>
TEXT2
<div id="div-02">Here is div-02</div>
<pre>Here is the result area</pre>
```

```js
// Initially, set node to the Text node with `TEXT`
let node = document.getElementById("div-01").previousSibling;

let result = "Next element siblings of TEXT:\n";

while (node) {
  result += `${node.nodeName}\n`;
  node = node.nextElementSibling; // The first node is a CharacterData, the others Element objects
}

document.querySelector("pre").textContent = result;
```

{{EmbedLiveSample("Example", "100%", "230")}}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("CharacterData.previousElementSibling")}}