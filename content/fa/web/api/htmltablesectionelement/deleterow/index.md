---
title: "HTMLTableSectionElement: deleteRow() method"
short-title: deleteRow()
slug: Web/API/HTMLTableSectionElement/deleteRow
page-type: web-api-instance-method
browser-compat: api.HTMLTableSectionElement.deleteRow
---

{{APIRef("HTML DOM")}}

متد **`deleteRow()`** از رابط {{domxref("HTMLTableSectionElement")}} یک ردیف مشخص ({{HtmlElement("tr")}}) را از یک {{HtmlElement("section")}} داده شده حذف می‌کند.

## نحو (Syntax)

```js-nolint
deleteRow(index)
```

### پارامترها

- `index`
  - : `index` یک عدد صحیح است که نشان‌دهنده ردیفی است که باید حذف شود. با این حال، از ایندکس ویژه `1-` می‌توان برای حذف آخرین ردیف بخش استفاده کرد.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

### استثناها (Exceptions)

- `IndexSizeError` {{domxref("DOMException")}}
  - : اگر `index` بزرگتر یا مساوی تعداد ردیف‌های موجود باشد یا یک مقدار منفی به غیر از `1-` باشد، پرتاب می‌شود.

## مثال‌ها

در این مثال، دو دکمه به شما امکان می‌دهند ردیف‌هایی را از بخش بدنه جدول اضافه و حذف کنید. همچنین یک عنصر {{HTMLElement("output")}} با تعداد ردیف‌های فعلی جدول به‌روزرسانی می‌شود.

### HTML

```html
<table>
  <thead>
    <tr>
      <th>ستون ۱</th>
      <th>ستون ۲</th>
      <th>ستون ۳</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>X</td>
      <td>Y</td>
      <td>Z</td>
    </tr>
  </tbody>
</table>
<button id="add">اضافه کردن ردیف</button>
<button id="remove">حذف آخرین ردیف</button>
<div>بدنه این جدول دارای <output>1</output> ردیف است.</div>
```

```css hidden
table {
  border-collapse: collapse;
}

th,
td {
  border: 1px solid black;
}

button {
  margin: 1em 1em 1em 0;
}
```

### JavaScript

```js
// دریافت عناصر رابط مرتبط
const bodySection = document.querySelectorAll("tbody")[0];
const rows = bodySection.rows; // مجموعه زنده است، بنابراین همیشه به‌روز است
const rowNumberDisplay = document.querySelectorAll("output")[0];

const addButton = document.getElementById("add");
const removeButton = document.getElementById("remove");

function updateRowNumber() {
  rowNumberDisplay.textContent = rows.length;
}

addButton.addEventListener("click", () => {
  // اضافه کردن یک ردیف جدید در انتهای بدنه
  const newRow = bodySection.insertRow();

  // اضافه کردن سلول‌ها درون ردیف جدید
  ["A", "B", "C"].forEach(
    (elt) => (newRow.insertCell().textContent = `${elt}${rows.length}`),
  );

  // به‌روزرسانی شمارنده ردیف
  updateRowNumber();
});

removeButton.addEventListener("click", () => {
  // حذف ردیف از بدنه
  bodySection.deleteRow(-1);

  // به‌روزرسانی شمارنده ردیف
  updateRowNumber();
});
```

### نتیجه

{{EmbedLiveSample("Examples", "100%", 175)}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLTableElement.deleteRow()")}}