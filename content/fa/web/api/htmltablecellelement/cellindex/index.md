---
title: "HTMLTableCellElement: cellIndex property"
short-title: cellIndex
slug: Web/API/HTMLTableCellElement/cellIndex
page-type: web-api-instance-property
browser-compat: api.HTMLTableCellElement.cellIndex
---

{{ APIRef("HTML DOM") }}

خاصیتِ فقط‌خواندنی **`cellIndex`** در رابط {{domxref("HTMLTableCellElement")}}، موقعیت یک سلول را درون ردیف ({{htmlelement("tr")}}) خود نشان می‌دهد. اولین سلول ایندکس `0` دارد.

## مقدار

ایندکس سلول را برمی‌گرداند، یا اگر سلول متعلق به هیچ ردیفی نباشد، مقدار `1-` را برمی‌گرداند.

## مثال‌ها

این مثال یک برچسب به شماره‌ی همه سلول‌های ردیف اول `tbody` اضافه می‌کند.

### HTML

```html
<table>
  <thead>
    <tr>
      <th>Item</th>
      <th>Price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Bananas</td>
      <td>$2</td>
    </tr>
    <tr>
      <td>Rice</td>
      <td>$2.5</td>
    </tr>
  </tbody>
</table>
```

```css hidden
table {
  border-collapse: collapse;
}

th,
td,
table {
  border: 1px solid black;
}

button {
  margin: 1em 1em 1em 0;
}
```

### JavaScript

```js
const rows = document.querySelectorAll("tbody tr");
const cells = rows[0].cells;

for (const cell of cells) {
  cell.textContent = `${cell.textContent} (cell #${cell.cellIndex})`;
}
```

### نتیجه

{{EmbedLiveSample("Examples")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}