---
title: "HTMLTableElement: deleteRow() method"
short-title: deleteRow()
slug: Web/API/HTMLTableElement/deleteRow
page-type: web-api-instance-method
browser-compat: api.HTMLTableElement.deleteRow
---

{{APIRef("HTML DOM")}}

متد **`HTMLTableElement.deleteRow()`** یک ردیف مشخص ({{HtmlElement("tr")}}) را از یک {{HtmlElement("table")}} حذف می‌کند.

## Syntax

```js-nolint
deleteRow(index)
```

### Parameters

- `index`
  - : `index` یک عدد صحیح است که نشان می‌دهد کدام ردیف باید حذف شود. با این حال، ایندکس ویژه `-1` را می‌توان برای حذف آخرین ردیف جدول استفاده کرد.

### Return value

هیچ ({{jsxref("undefined")}}).

### Exceptions

- `IndexSizeError` {{domxref("DOMException")}}
  - : اگر `index` بزرگ‌تر یا مساوی تعداد ردیف‌های موجود باشد یا یک مقدار منفی به غیر از `-1` باشد، پرتاب می‌شود.

## Examples

این مثال از جاوااسکریپت برای حذف ردیف دوم یک جدول استفاده می‌کند.

### HTML

```html
<table>
  <tbody>
    <tr>
      <td>Cell 1.1</td>
      <td>Cell 1.2</td>
      <td>Cell 1.3</td>
    </tr>
    <tr>
      <td>Cell 2.1</td>
      <td>Cell 2.2</td>
      <td>Cell 2.3</td>
    </tr>
    <tr>
      <td>Cell 3.1</td>
      <td>Cell 3.2</td>
      <td>Cell 3.3</td>
    </tr>
  </tbody>
</table>
```

### JavaScript

```js
let table = document.querySelector("table");

// Delete second row
table.deleteRow(1);
```

### Result

{{EmbedLiveSample("Examples")}}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("HTMLTableSectionElement.deleteRow()")}}