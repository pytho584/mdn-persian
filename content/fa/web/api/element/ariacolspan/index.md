---
title: "Element: ariaColSpan property"
short-title: ariaColSpan
slug: Web/API/Element/ariaColSpan
page-type: web-api-instance-property
browser-compat: api.Element.ariaColSpan
---

{{APIRef("DOM")}}

ویژگی **`ariaColSpan`** از رابط {{domxref("Element")}}، مقدار ویژگی [`aria-colspan`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colspan) را منعکس می‌کند؛ ویژگی‌ای که تعداد ستون‌های پوشش‌داده‌شده توسط یک سلول (cell) یا سلول شبکه‌ای (gridcell) را در یک جدول (table)، شبکه (grid) یا درخت‌شبکه (treegrid) تعیین می‌کند.

## مقدار

یک رشته (string) که یک عدد صحیح (integer) را شامل می‌شود.

## مثال‌ها

در این مثال، ویژگی `aria-colspan` روی عنصری با شناسه‌ی `spanning-heading` برابر «2» تنظیم شده است. با استفاده از `ariaColSpan` مقدار آن را به «3» به‌روزرسانی می‌کنیم.

```html
<table>
  <thead>
    <tr>
      <th>Heading 1</th>
      <th>Heading 2</th>
      <th>Heading 3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td colspan="2" aria-colspan="2" id="spanning-column">Spanning</td>
      <td>One</td>
    </tr>
  </tbody>
</table>
```

```js
let el = document.getElementById("spanning-column");
console.log(el.ariaColSpan);
el.ariaColSpan = "3";
console.log(el.ariaColSpan);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- [نقش جدول (table) در ARIA](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/table_role)