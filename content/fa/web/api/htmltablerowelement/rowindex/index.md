---
title: "HTMLTableRowElement: rowIndex property"
short-title: rowIndex
slug: Web/API/HTMLTableRowElement/rowIndex
page-type: web-api-instance-property
browser-compat: api.HTMLTableRowElement.rowIndex
---

{{ APIRef("HTML DOM") }}

خاصیت فقط‌خواندنی **`rowIndex`** از رابط {{domxref("HTMLTableRowElement")}} موقعیت یک سطر را در کل {{HtmlElement("table")}} نشان می‌دهد.

حتی وقتی عناصر {{HtmlElement("thead")}}، {{HtmlElement("tbody")}} و {{HtmlElement("tfoot")}} در HTML به‌هم‌ریخته باشند، مرورگرها جدول را به ترتیب درست رندر می‌کنند. بنابراین شمارش سطرها از `<thead>` به `<tbody>` و از `<tbody>` به `<tfoot>` انجام می‌شود.

## مقدار

شاخص سطر، یا `۱-` اگر سطر بخشی از جدول نباشد.

## مثال‌ها

این مثال با استفاده از جاوااسکریپت شماره‌ی همه‌ی سطرهای یک جدول را برچسب‌گذاری می‌کند.

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
      <td>Oranges</td>
      <td>$8</td>
    </tr>
    <tr>
      <td>Top Sirloin</td>
      <td>$20</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <td>Total</td>
      <td>$30</td>
    </tr>
  </tfoot>
</table>
```

### JavaScript

```js
const rows = document.querySelectorAll("tr");

rows.forEach((row) => {
  const z = document.createElement("td");
  z.textContent = `(row #${row.rowIndex})`;
  row.appendChild(z);
});
```

### نتیجه

{{EmbedLiveSample("Examples")}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLTableRowElement.sectionRowIndex")}}