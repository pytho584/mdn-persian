---
title: "Element.ariaRowIndexText"
---

---
title: Element.ariaRowIndexText
slug: Web/API/Element/ariaRowIndexText
page-type: web-api-instance-property
browser-compat: api.Element.ariaRowIndexText
---

{{APIRef("DOM")}}

ویژگی **`ariaRowIndexText`** از رابط {{domxref("Element")}} مقدار ویژگی [`aria-rowindextext`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowindextext) را منعکس می‌کند که جایگزین متنی قابل‌خواندن برای انسان به‌جای `aria-rowindex` تعریف می‌کند.

## مقدار

یک رشته.

## مثال‌ها

در این مثال، ویژگی `aria-rowindextext` روی عنصری با شناسهٔ `role-heading` روی «Heading row» تنظیم شده است. با استفاده از `ariaRowIndexText` مقدار را به «Updated heading row» به‌روزرسانی می‌کنیم.

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
        aria-rowindextext="Heading row">
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
console.log(el.ariaRowIndexText); // "Heading row"
el.ariaRowIndexText = "Updated heading row";
console.log(el.ariaRowIndexText); // "Updated heading row"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [نقش جدول ARIA](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/table_role)