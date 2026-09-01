---
title: "HTMLOListElement: reversed property"
short-title: reversed
slug: Web/API/HTMLOListElement/reversed
page-type: web-api-instance-property
browser-compat: api.HTMLOListElement.reversed
---

{{ApiRef("HTML DOM")}}

ویژگی **`reversed`** در رابط {{domxref("HTMLOListElement")}} ترتیب یک فهرست را نشان می‌دهد.

این ویژگی منعکس‌کنندهٔ ویژگی [`reversed`](/en-US/docs/Web/HTML/Reference/Elements/ol#reversed) عنصر {{HTMLElement("ol")}} است.

## مقدار

یک مقدار بولی (`boolean`). اگر `true` باشد، نشان می‌دهد که فهرست به صورت نزولی (..., 3, 2, 1) است.

## نمونه‌ها

### HTML

```html
<ol id="order-list">
  <li>Fee</li>
  <li>Fi</li>
  <li>Fo</li>
  <li>Fum</li>
</ol>
```

### JavaScript

```js
const olElement = document.querySelector("#order-list");
console.log(olElement.reversed); // Output: "false"
olElement.reversed = "true";
console.log(olElement.reversed); // Output: "true"
```

### نتیجه

{{EmbedLiveSample("Examples", 400, 100)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}