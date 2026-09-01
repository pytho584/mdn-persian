---
title: "Element: ariaSort property"
short-title: ariaSort
slug: Web/API/Element/ariaSort
page-type: web-api-instance-property
browser-compat: api.Element.ariaSort
---

{{APIRef("DOM")}}

ویژگی **`ariaSort`** در رابط {{domxref("Element")}} منعکس‌کنندهٔ مقدار ویژگی [`aria-sort`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-sort) است که نشان می‌دهد آیا آیتم‌های یک جدول یا شبکه به‌ترتیب صعودی یا نزولی مرتب شده‌اند.

## مقدار

یک رشته (string) با یکی از مقادیر زیر:

- `"ascending"`
  - : آیتم‌ها بر اساس این ستون به‌ترتیب صعودی مرتب شده‌اند.
- `"descending"`
  - : آیتم‌ها بر اساس این ستون به‌ترتیب نزولی مرتب شده‌اند.
- `"none"`
  - : هیچ ترتیب مرتب‌سازی مشخصی برای این ستون اعمال نشده است.
- `"other"`
  - : الگوریتم مرتب‌سازی دیگری به‌جز صعودی یا نزولی اعمال شده است.

## مثال‌ها

در این مثال، ویژگی `aria-sort` روی عنصری که شناسهٔ آن `role-heading` است، روی «none» تنظیم شده است. با استفاده از `ariaSort` مقدار آن را به «ascending» به‌روزرسانی می‌کنیم.

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
console.log(el.ariaSort); // none
el.ariaSort = "ascending";
console.log(el.ariaSort); // ascending
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [نقش table در ARIA](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/table_role)