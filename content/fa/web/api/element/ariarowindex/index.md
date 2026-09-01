---
title: "Element: ariaRowIndex property"
short-title: ariaRowIndex
slug: Web/API/Element/ariaRowIndex
page-type: web-api-instance-property
browser-compat: api.Element.ariaRowIndex
---

{{APIRef("DOM")}}

ویژگی **`ariaRowIndex`** از رابط {{domxref("Element")}} مقدار ویژگی [`aria-rowindex`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowindex) را نشان می‌دهد؛ این ویژگی شاخص سطر یک عنصر یا موقعیت آن را نسبت به تعداد کل سطرها در یک جدول، گرید یا treegrid تعیین می‌کند.

## مقدار

یک رشته (string) که شامل یک عدد صحیح است.

## مثال‌ها

در این مثال، ویژگی `aria-rowindex` روی عنصری با شناسهٔ `role-heading` به "1" تنظیم شده است. با استفاده از `ariaRowIndex` مقدار را به "2" تغییر می‌دهیم.

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
        aria-rowindex="1">
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
console.log(el.ariaRowIndex); // 1
el.ariaRowIndex = "2";
console.log(el.ariaRowIndex); // 2
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [نقش جدول در ARIA](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/table_role)