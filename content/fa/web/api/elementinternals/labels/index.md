---
title: "ElementInternals: labels property"
short-title: labels
slug: Web/API/ElementInternals/labels
page-type: web-api-instance-property
browser-compat: api.ElementInternals.labels
---

{{APIRef("Web Components")}}

ویژگی فقط‌خواندنی **`labels`** از رابط {{domxref("ElementInternals")}}، برچسب‌های مرتبط با عنصر را بازمی‌گرداند.

## مقدار

یک {{domxref("NodeList")}} شامل تمام عناصر برچسب (label) مرتبط با این عنصر.

## مثال‌ها

مثال زیر یک مؤلفه چک‌باکس سفارشی را نشان می‌دهد که یک عنصر {{HTMLElement("label")}} به آن متصل شده است.
چاپ مقدار `labels` در کنسول یک {{domxref("NodeList")}} با یک ورودی را بازمی‌گرداند که نمایانگر این برچسب است.

```html
<form id="myForm">
  <custom-checkbox id="custom-checkbox"></custom-checkbox>
  <label for="custom-checkbox">Join newsletter</label>
</form>
```

```js
let element = document.getElementById("custom-checkbox");
console.log(element.internals_.label);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}