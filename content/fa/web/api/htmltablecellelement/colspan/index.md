---
title: "HTMLTableCellElement: colSpan property"
short-title: colSpan
slug: Web/API/HTMLTableCellElement/colSpan
page-type: web-api-instance-property
browser-compat: api.HTMLTableCellElement.colSpan
---

{{ APIRef("HTML DOM") }}

ویژگی **`colSpan`** از رابط {{domxref("HTMLTableCellElement")}} نشان‌دهندهٔ تعداد ستون‌هایی است که این سلول باید گسترش یابد؛ این ویژگی به سلول اجازه می‌دهد فضای چندین ستون جدول را اشغال کند. این ویژگی منعکس‌کنندهٔ ویژگی [`colspan`](/en-US/docs/Web/HTML/Reference/Elements/td#colspan) است.

## مقدار

یک عدد مثبت که تعداد ستون‌ها را نشان می‌دهد.

> [!NOTE]
> هنگام تنظیم یک مقدار جدید، مقدار به نزدیک‌ترین عدد کاملاً مثبت _محدود_ می‌شود.

## مثال‌ها

این مثال دو دکمه برای تغییر گستردگی ستون (colspan) اولین سلول بدنهٔ جدول ارائه می‌دهد.

### HTML

```html
<table>
  <thead>
    <tr>
      <th>ستون ۱</th>
      <th>ستون ۲</th>
      <th>ستون ۳</th>
      <th>ستون ۴</th>
      <th>ستون ۵</th>
      <th>ستون ۶</th>
      <th>ستون ۷</th>
      <th>ستون ۸</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td colspan="2">۱</td>
      <td>۲</td>
      <td>۳</td>
      <td>۴</td>
      <td>۵</td>
      <td>۶</td>
      <td>۷</td>
      <td>۸</td>
    </tr>
  </tbody>
</table>
<button id="increase">افزایش colspan</button>
<button id="decrease">کاهش colspan</button>
<div>اولین سلول <output>۲</output> ستون را پوشش می‌دهد.</div>
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
// دریافت عناصر رابط مورد نظر
const cell = document.querySelectorAll("tbody tr td")[0];
const output = document.querySelectorAll("output")[0];

const increaseButton = document.getElementById("increase");
const decreaseButton = document.getElementById("decrease");

increaseButton.addEventListener("click", () => {
  cell.colSpan += 1;

  // به‌روزرسانی نمایش
  output.textContent = cell.colSpan;
});

decreaseButton.addEventListener("click", () => {
  cell.colSpan -= 1;

  // به‌روزرسانی نمایش
  output.textContent = cell.colSpan;
});
```

### نتیجه

{{EmbedLiveSample("Examples", "100%", 175)}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("HTMLTableCellElement.rowSpan")}}
- {{domxref("HTMLTableColElement.span")}}