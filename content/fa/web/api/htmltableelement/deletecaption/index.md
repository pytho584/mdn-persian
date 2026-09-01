---
title: "HTMLTableElement: deleteCaption() method"
---

---
title: "HTMLTableElement: deleteCaption() method"
short-title: deleteCaption()
slug: Web/API/HTMLTableElement/deleteCaption
page-type: web-api-instance-method
browser-compat: api.HTMLTableElement.deleteCaption
---

{{APIRef("HTML DOM")}}

متد **`HTMLTableElement.deleteCaption()`** عنصر {{HtmlElement("caption")}} را از یک {{HtmlElement("table")}} حذف می‌کند. اگر عنصر `<caption>` مرتبطی با جدول وجود نداشته باشد، این متد هیچ کاری انجام نمی‌دهد.

## نحو

```js-nolint
deleteCaption()
```

### پارامترها

هیچ.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

این مثال از جاوااسکریپت برای حذف عنوان (caption) یک جدول استفاده می‌کند.

### HTML

```html
<table>
  <caption>
    This caption will be deleted!
  </caption>
  <tbody>
    <tr>
      <td>Cell 1.1</td>
      <td>Cell 1.2</td>
    </tr>
    <tr>
      <td>Cell 2.1</td>
      <td>Cell 2.2</td>
    </tr>
  </tbody>
</table>
```

### JavaScript

```js
let table = document.querySelector("table");
table.deleteCaption();
```

### نتیجه

{{EmbedLiveSample("Examples")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}