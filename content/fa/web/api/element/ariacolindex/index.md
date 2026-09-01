---
title: "Element: ariaColIndex property"
short-title: ariaColIndex
slug: Web/API/Element/ariaColIndex
page-type: web-api-instance-property
browser-compat: api.Element.ariaColIndex
---

{{APIRef("DOM")}}

ویژگی **`ariaColIndex`** در رابط {{domxref("Element")}} مقدار ویژگی [`aria-colindex`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colindex) را منعکس می‌کند؛ این ویژگی ایندکس یا موقعیت ستون یک عنصر را نسبت به تعداد کل ستون‌های موجود در یک جدول، شبکه (grid) یا شبکه درختی (treegrid) تعریف می‌کند.

## مقدار

یک رشته (string) که شامل یک عدد صحیح است.

## مثال‌ها

در این مثال، ویژگی `aria-colindex` روی عنصری با شناسه (ID) «role-heading» به مقدار «1» تنظیم شده است. با استفاده از `ariaColIndex` مقدار آن را به «2» تغییر می‌دهیم.

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
      <th
        role="columnheader"
        id="role-heading"
        aria-sort="none"
        aria-rowindex="1"
        aria-colindex="1">
        ARIA Role
      </th>
      <th
        role="columnheader"
        id="element-heading"
        aria-sort="none"
        aria-rowindex="1">
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
let el = document.getElementById("role-heading");
console.log(el.ariaColIndex); // 1
el.ariaColIndex = "2";
console.log(el.ariaColIndex); // 2
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [ARIA: table role](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/table_role)