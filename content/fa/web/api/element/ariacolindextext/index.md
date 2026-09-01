---
title: "Element.ariaColIndexText"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Element/ariaColIndexText"
---

---
title: Element.ariaColIndexText
slug: Web/API/Element/ariaColIndexText
page-type: web-api-instance-property
browser-compat: api.Element.ariaColIndexText
---

{{APIRef("DOM")}}

ویژگی **`ariaColIndexText`** در رابط {{domxref("Element")}} مقدار ویژگی [`aria-colindextext`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colindextext) را منعکس می‌کند؛ ویژگی‌ای که یک جایگزین متنی قابل‌فهم برای انسان به‌جای `aria-colindex` تعریف می‌کند.

## مقدار

یک رشته (string).

## مثال‌ها

در این مثال، ویژگی `aria-colindex` روی عنصری با شناسه `role-heading` به مقدار «Aria Role column» تنظیم شده است. با استفاده از `ariaColIndexText` مقدار را به رشته «New column name» به‌روزرسانی می‌کنیم.

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
        aria-colindex="1"
        aria-colindextext="Aria Role column">
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
console.log(el.ariaColIndexText); // "Aria Role"
el.ariaColIndexText = "New column name";
console.log(el.ariaColIndexText); // "New column name"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [ARIA: نقش جدول](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/table_role)