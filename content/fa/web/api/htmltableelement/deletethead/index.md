---
title: "HTMLTableElement: deleteTHead() method"
short-title: deleteTHead()
slug: Web/API/HTMLTableElement/deleteTHead
page-type: web-api-instance-method
browser-compat: api.HTMLTableElement.deleteTHead
---

{{APIRef("HTML DOM")}}

متد **`HTMLTableElement.deleteTHead()`** عنصر {{HTMLElement("thead")}} را از یک جدول معین حذف می‌کند.

## سینتکس

```js-nolint
deleteTHead()
```

### پارامترها

هیچ.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

این مثال از JavaScript برای حذف سربرگ یک جدول استفاده می‌کند.

### HTML

```html
<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Occupation</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Bob</td>
      <td>Plumber</td>
    </tr>
    <tr>
      <td>Jim</td>
      <td>Roofer</td>
    </tr>
  </tbody>
</table>
```

### JavaScript

```js
let table = document.querySelector("table");
table.deleteTHead();
```

### نتیجه

{{EmbedLiveSample("Examples")}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}