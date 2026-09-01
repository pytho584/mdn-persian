---
title: "DocumentFragment: firstElementChild property"
---

---
title: "DocumentFragment: firstElementChild property"
short-title: firstElementChild
slug: Web/API/DocumentFragment/firstElementChild
page-type: web-api-instance-property
browser-compat: api.DocumentFragment.firstElementChild
---

{{ APIRef("DOM") }}

ویژگی فقط‌خواندنی **`DocumentFragment.firstElementChild`** نخستین فرزندِ {{domxref("Element")}} متعلق به قطعه سند را برمی‌گرداند؛ یا اگر هیچ عنصر فرزندی وجود نداشته باشد، `null` را برمی‌گرداند.

## مقدار

یک {{domxref("Element")}} که نخستین فرزندِ `Element` آن شیء است، یا اگر هیچ‌کدام وجود نداشته باشد، `null`.

## مثال‌ها

```js
let fragment = new DocumentFragment();
fragment.firstElementChild; // null

let paragraph = document.createElement("p");
fragment.appendChild(paragraph);

fragment.firstElementChild; // <p>
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Element.firstElementChild")}}