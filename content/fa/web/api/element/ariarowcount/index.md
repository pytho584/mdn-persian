---
title: "Element: ariaRowCount property"
short-title: ariaRowCount
slug: Web/API/Element/ariaRowCount
page-type: web-api-instance-property
browser-compat: api.Element.ariaRowCount
---

{{APIRef("DOM")}}

ویژگی **`ariaRowCount`** از رابط {{domxref("Element")}} منعکس‌کنندهٔ مقدار ویژگی [`aria-rowcount`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowcount) است که تعداد کل ردیف‌ها را در یک جدول، گرید یا درخت‌گرید تعریف می‌کند.

## مقدار

یک رشته که شامل یک عدد صحیح است.

## مثال‌ها

در این مثال، ویژگی `aria-rowcount` روی عنصر با شناسهٔ `semantic-table` برابر با «100» تنظیم شده است که تعداد کل ردیف‌های جدول را نشان می‌دهد، نه ردیف‌های قابل مشاهدهٔ فعلی را. با استفاده از `ariaRowCount` مقدار را به «101» به‌روزرسانی می‌کنیم.

```html
<table
  id="semantic-table"
  role="table"
  aria-label="Semantic Elements"
  aria-describedby="semantic_elements_table_desc"
  aria-rowcount="100">
  <caption id="semantic_elements_table_desc">
    Semantic Elements to use instead of ARIA's roles
  </caption>
  <thead role="rowgroup">
    <tr role="row">
      <th role="columnheader" aria-sort="none" aria-rowindex="1">ARIA Role</th>
      <th role="columnheader" aria-sort="none" aria-rowindex="1">
        Semantic Element
      </th>
    </tr>
  </thead>
  <tbody role="rowgroup">
    <tr role="row">
      <td role="cell" aria-rowindex="11">header</td>
      <td role="cell" aria-rowindex="11">h1</td>
    </tr>
    <tr role="row">
      <td role="cell" aria-rowindex="16">header</td>
      <td role="cell" aria-rowindex="16">h6</td>
    </tr>
    <tr role="row">
      <td role="cell" aria-rowindex="18">rowgroup</td>
      <td role="cell" aria-rowindex="18">thead</td>
    </tr>
    <tr role="row">
      <td role="cell" aria-rowindex="24">term</td>
      <td role="cell" aria-rowindex="24">dt</td>
    </tr>
  </tbody>
</table>
```

```js
let el = document.getElementById("semantic-table");
console.log(el.ariaRowCount); // 100
el.ariaRowCount = "101";
console.log(el.ariaRowCount); // 101
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [ARIA: نقش table](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/table_role)