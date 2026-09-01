---
title: "DocumentFragment: children property"
short-title: children
slug: Web/API/DocumentFragment/children
page-type: web-api-instance-property
browser-compat: api.DocumentFragment.children
---

{{ APIRef("DOM") }}

ویژگی فقط‌خواندنی **`children`** یک {{domxref("HTMLCollection")}} زنده را برمی‌گرداند که شامل همهٔ {{domxref("Element", "elements")}} فرزندِ قطعه سند (document fragment) است که روی آن فراخوانی شده است.

## مقدار

یک {{ domxref("HTMLCollection") }} که مجموعهٔ زنده و مرتبی از عنصرهای DOM است که فرزندِ قطعه سند هستند. می‌توانید به گره‌های فرزندِ منفرد در این مجموعه یا با متد {{domxref("HTMLCollection.item()", "item()")}} روی خود مجموعه دسترسی پیدا کنید، یا از نماد آرایه‌مانند جاوااسکریپت استفاده کنید.

اگر قطعه سند هیچ عنصر فرزندی نداشته باشد، `children` یک فهرست خالی با `length` برابر با `0` است.

## مثال‌ها

```js
let fragment = new DocumentFragment();
fragment.children; // HTMLCollection []

let paragraph = document.createElement("p");
fragment.appendChild(paragraph);

fragment.children; // HTMLCollection [<p>]
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Node.childNodes")}}