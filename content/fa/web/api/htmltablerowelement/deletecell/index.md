---
title: "HTMLTableRowElement: deleteCell() method"
short-title: deleteCell()
slug: Web/API/HTMLTableRowElement/deleteCell
page-type: web-api-instance-method
browser-compat: api.HTMLTableRowElement.deleteCell
---

{{APIRef("HTML DOM")}}

متد **`deleteCell()`** در رابط {{domxref("HTMLTableRowElement")}} یک سلول مشخص از ردیف را از یک عنصر {{htmlelement("tr")}} حذف می‌کند.

## نحو (Syntax)

```js-nolint
deleteCell(index)
```

### پارامترها

- `index`
  - : اندیس سلولی که باید حذف شود. اگر `index` برابر با `-1` یا برابر با تعداد سلول‌ها باشد، آخرین سلول ردیف حذف می‌شود.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها (Exceptions)

- `IndexSizeError` {{domxref("DOMException")}}
  - : اگر `index` بزرگ‌تر از تعداد سلول‌ها یا کوچک‌تر از `-1` باشد پرتاب می‌شود.

## مثال‌ها

این مثال از {{domxref("HTMLTableRowElement.insertCell()")}} برای افزودن یک سلول جدید به یک ردیف استفاده می‌کند.

### HTML

```html
<table>
  <thead>
    <tr>
      <th>C1</th>
      <th>C2</th>
      <th>C3</th>
      <th>C4</th>
      <th>C5</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Cell 1</td>
      <td>Cell 2</td>
    </tr>
  </tbody>
</table>

<button id="add">Add a cell</button>
<button id="remove">Remove last cell</button>
<div>This first row has <output>2</output> cell(s).</div>
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
// Obtain relevant interface elements
const bodySection = document.querySelectorAll("tbody")[0];
const row = bodySection.rows[0]; // Select the first row of the body section
const cells = row.cells; // The collection is live, therefore always up-to-date
const cellNumberDisplay = document.querySelectorAll("output")[0];

const addButton = document.getElementById("add");
const removeButton = document.getElementById("remove");

function updateCellNumber() {
  cellNumberDisplay.textContent = cells.length;
}

addButton.addEventListener("click", () => {
  // Add a new cell at the end of the first row
  const newCell = row.insertCell();
  newCell.textContent = `Cell ${cells.length}`;

  // Update the row counter
  updateCellNumber();
});

removeButton.addEventListener("click", () => {
  // Delete the row from the body
  row.deleteCell(-1);

  // Update the row counter
  updateCellNumber();
});
```

### نتیجه

{{EmbedLiveSample("Examples", "100%", 175)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLTableElement.insertRow()")}}
- عنصر HTML نمایانگر سلول‌ها: {{domxref("HTMLTableCellElement")}}