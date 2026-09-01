---
title: "HTMLTableElement: tBodies property"
short-title: tBodies
slug: Web/API/HTMLTableElement/tBodies
page-type: web-api-instance-property
browser-compat: api.HTMLTableElement.tBodies
---

{{APIRef("HTML DOM")}}

ویژگی فقط‌خواندنی **`HTMLTableElement.tBodies`** یک {{domxref("HTMLCollection")}} زنده از بدنه‌های یک {{htmlElement("table")}} را برمی‌گرداند.

اگرچه این ویژگی فقط‌خواندنی است، اما شیء بازگشتی زنده بوده و امکان تغییر محتوای آن وجود دارد.

مجموعه‌ی بازگشتی شامل عناصر {{HTMLElement("tbody")}} ضمنی نیز می‌شود. برای مثال:

```html
<table>
  <tr>
    <td>cell one</td>
  </tr>
</table>
```

DOM تولیدشده از HTML فوق شامل یک عنصر {{HTMLElement("tbody")}} خواهد بود، حتی اگر این تگ‌ها در HTML منبع وجود نداشته باشند.

## مقدار

یک {{domxref("HTMLCollection")}} زنده.

## مثال‌ها

این قطعه‌کد تعداد بدنه‌های یک جدول را به دست می‌آورد.

```js
myTable.tBodies.length;
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLCollection")}}
- {{HTMLElement("tbody")}}