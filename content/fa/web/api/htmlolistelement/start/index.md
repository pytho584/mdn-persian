---
title: "HTMLOListElement: start property"
short-title: start
slug: Web/API/HTMLOListElement/start
page-type: web-api-instance-property
browser-compat: api.HTMLOListElement.start
---

{{ApiRef("HTML DOM")}}

ویژگی **`start`** در رابط {{domxref("HTMLOListElement")}} مقدار شروع لیست مرتب را مشخص می‌کند. مقدار پیش‌فرض آن ۱ است.

این ویژگی منعکس‌کنندهٔ ویژگی [`start`](/en-US/docs/Web/HTML/Reference/Elements/ol#start) عنصر {{HTMLElement("ol")}} است.

> [!NOTE]
> مقدار ویژگی `start` مستقل از ویژگی {{domxref("HTMLOListElement.type")}} است؛ همیشه عددی است، حتی زمانی که نوع حروف یا اعداد رومی باشد.

## مقدار

یک مقدار از نوع `long`.

## مثال‌ها

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
console.log(olElement.start); // خروجی: "1"
olElement.start = "11";
console.log(olElement.start); // خروجی: "11"
```

### نتیجه

{{EmbedLiveSample("Examples", 400, 100)}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}