---
title: "HTMLTableRowElement: sectionRowIndex property"
short-title: sectionRowIndex
slug: Web/API/HTMLTableRowElement/sectionRowIndex
page-type: web-api-instance-property
browser-compat: api.HTMLTableRowElement.sectionRowIndex
---

{{ APIRef("HTML DOM") }}

ویژگی فقط‌خواندنی **`sectionRowIndex`** در رابط {{domxref("HTMLTableRowElement")}} نشان‌دهندهٔ موقعیت یک ردیف در بخش فعلی جدول است ({{htmlelement("thead")}}، {{htmlelement("tbody")}} یا {{htmlelement("tfoot")}}).

## مقدار

اندیس ردیف، یا `1-` اگر ردیف بخشی از آن بخش نباشد.

## مثال‌ها

این مثال با استفاده از جاوااسکریپت، شمارهٔ همهٔ ردیف‌های `tbody` را برچسب‌گذاری می‌کند.

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
const rows = document.querySelectorAll("tbody tr");

rows.forEach((row) => {
  const z = document.createElement("td");
  z.textContent = `(row #${row.sectionRowIndex})`;
  row.appendChild(z);
});
```

### نتیجه

{{EmbedLiveSample("Examples")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("HTMLTableRowElement.rowIndex")}}