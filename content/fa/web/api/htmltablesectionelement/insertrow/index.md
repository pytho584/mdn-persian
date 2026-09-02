---
title: "HTMLTableSectionElement: insertRow() method"
short-title: insertRow()
slug: Web/API/HTMLTableSectionElement/insertRow
page-type: web-api-instance-method
browser-compat: api.HTMLTableSectionElement.insertRow
---

{{APIRef("HTML DOM")}}

متد **`insertRow()`** از رابط {{domxref("HTMLTableSectionElement")}} یک ردیف جدید ({{HtmlElement("tr")}}) را در عنصر بخش‌بندی جدولِ داده‌شده ({{HTMLElement("thead")}}، {{HTMLElement("tfoot")}} یا {{HTMLElement("tbody")}}) درج می‌کند و سپس یک ارجاع به این ردیف جدید بازمی‌گرداند.

> [!NOTE]
> `insertRow()` ردیف را مستقیماً در بخش درج می‌کند. برخلاف حالتی که برای ایجاد عنصر `<tr>` جدید از {{domxref("Document.createElement()")}} استفاده می‌شود، ردیف نیازی به افزوده‌شدنِ جداگانه ندارد.

## Syntax

```js-nolint
insertRow()
insertRow(index)
```

### Parameters

- `index` {{optional_inline}}
  - : شاخص ردیف جدید. اگر `index` برابر با `-1` یا برابر با تعداد ردیف‌ها باشد، ردیف به‌عنوان آخرین ردیف اضافه می‌شود. اگر `index` حذف شود، مقدار پیش‌فرض آن `-1` است.

### Return value

یک {{domxref("HTMLTableRowElement")}} که به ردیف جدید ارجاع می‌دهد.

### Exceptions

- `IndexSizeError` {{domxref("DOMException")}}
  - : اگر `index` بزرگ‌تر از تعداد ردیف‌ها یا کوچک‌تر از `-1` باشد، این استثنا پرتاب می‌شود.

## Examples

در این مثال، دو دکمه به شما امکان می‌دهند ردیف‌هایی را به بخش بدنهٔ جدول اضافه یا از آن حذف کنید؛ همچنین یک عنصر {{HTMLElement("output")}} را با تعداد ردیف‌های موجود در جدول به‌روزرسانی می‌کند.

### HTML

```html
<table>
  <thead>
    <tr>
      <th>Col 1</th>
      <th>Col 2</th>
      <th>Col 3</th>
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
<button id="add">Add a row</button>
<button id="remove">Remove last row</button>
<div>This table's body has <output>1</output> row(s).</div>
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
// Obtain relevant interface elements
const bodySection = document.querySelectorAll("tbody")[0];
const rows = bodySection.rows; // The collection is live, therefore always up-to-date
const rowNumberDisplay = document.querySelectorAll("output")[0];

const addButton = document.getElementById("add");
const removeButton = document.getElementById("remove");

function updateRowNumber() {
  rowNumberDisplay.textContent = rows.length;
}

addButton.addEventListener("click", () => {
  // Add a new row at the end of the body
  const newRow = bodySection.insertRow();

  // Add cells inside the new row
  ["A", "B", "C"].forEach(
    (elt) => (newRow.insertCell().textContent = `${elt}${rows.length}`),
  );

  // Update the row counter
  updateRowNumber();
});

removeButton.addEventListener("click", () => {
  // Delete the row from the body
  bodySection.deleteRow(-1);

  // Update the row counter
  updateRowNumber();
});
```

### Result

{{EmbedLiveSample("Examples", "100%", 175)}}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("HTMLTableRowElement.insertCell()")}}
- {{domxref("HTMLTableElement.insertRow()")}}