---
title: "HTMLOListElement: type property"
short-title: type
slug: Web/API/HTMLOListElement/type
page-type: web-api-instance-property
browser-compat: api.HTMLOListElement.type
---

{{ApiRef("HTML DOM")}}

ویژگی **`type`** در رابط {{domxref("HTMLOListElement")}} نوع نشانگری را که برای نمایش فهرست مرتب استفاده می‌شود مشخص می‌کند.

این ویژگی بازتاب‌دهندهٔ ویژگی [`type`](/en-US/docs/Web/HTML/Reference/Elements/ol#type) عنصر {{HTMLElement("ol")}} است.

> [!NOTE]
> مقدار `type` را می‌توان با ویژگی CSS {{CSSxRef("list-style-type")}} تعریف کرد. ویژگی `list-style-type` مقادیر بسیار بیشتری در اختیار قرار می‌دهد.

## مقدار

یک رشته (string) که نوع را مشخص می‌کند.

مقادیر ممکن آن در بخش [انواع نشانگر](/en-US/docs/Web/HTML/Reference/Elements/ol#type) از ویژگی `type` فهرست شده‌اند.

## Examples

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
// if type is not specified then return empty string
console.log(olElement.type); // Output: ""
olElement.type = "i"; // Using roman numeral type
console.log(olElement.type); // Output: "i"
```

### نتیجه

{{EmbedLiveSample("Examples", 400, 100)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}