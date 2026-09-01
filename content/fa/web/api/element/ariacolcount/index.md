---
title: "Element: ariaColCount property"
short-title: ariaColCount
slug: Web/API/Element/ariaColCount
page-type: web-api-instance-property
browser-compat: api.Element.ariaColCount
---

{{APIRef("DOM")}}

ویژگی **`ariaColCount`** از رابط {{domxref("Element")}} منعکس‌کننده مقدار ویژگی [`aria-colcount`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colcount) است که تعداد ستون‌ها را در یک جدول، شبکه (grid) یا شبکه درختی (treegrid) تعریف می‌کند.

## مقدار

یک رشته (string).

## مثال‌ها

در این مثال، ویژگی `aria-colcount` روی عنصری با شناسه `semantic-table` برابر با "2" تنظیم شده است. با استفاده از `ariaColCount` مقدار را به "3" به‌روزرسانی می‌کنیم.

```html
<table
  id="semantic-table"
  role="table"
  aria-label="Semantic Elements"
  aria-describedby="semantic_elements_table_desc"
  aria-rowcount="100"
  aria-colcount="2">
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
console.log(el.ariaColCount); // 2
el.ariaColCount = "3";
console.log(el.ariaColCount); // 3
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [ARIA: نقش table](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/table_role)