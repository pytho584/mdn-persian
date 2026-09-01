---
title: "DocumentFragment: lastElementChild property"
short-title: lastElementChild
slug: Web/API/DocumentFragment/lastElementChild
page-type: web-api-instance-property
browser-compat: api.DocumentFragment.lastElementChild
---

{{ APIRef("DOM") }}

ویژگی فقط‌خواندنی **`DocumentFragment.lastElementChild`** آخرین فرزند {{domxref("Element")}} از این قطعه سند (document fragment) را برمی‌گرداند، یا اگر هیچ عنصر فرزندی وجود نداشته باشد، `null` را برمی‌گرداند.

## مقدار

یک {{domxref("Element")}} که آخرین `Element` فرزند این شیء است، یا اگر هیچ‌کدام وجود نداشته باشد `null`.

## مثال‌ها

```js
let fragment = new DocumentFragment();
fragment.lastElementChild; // null

let paragraph = document.createElement("p");
fragment.appendChild(paragraph);

fragment.lastElementChild; // <p>
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Element.lastElementChild")}}