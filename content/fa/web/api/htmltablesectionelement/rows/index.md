---
title: "HTMLTableSectionElement: rows property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/HTMLTableSectionElement/rows"
---

---
title: "HTMLTableSectionElement: rows property"
short-title: rows
slug: Web/API/HTMLTableSectionElement/rows
page-type: web-api-instance-property
browser-compat: api.HTMLTableSectionElement.rows
---

{{APIRef("HTML DOM")}}

خاصیتِ فقط‌خواندنی **`rows`** در رابط {{domxref("HTMLTableSectionElement")}} یک {{domxref("HTMLCollection")}} زنده برمی‌گرداند که شامل ردیف‌های آن بخش است. `HTMLCollection` زنده است و با اضافه یا حذف شدن ردیف‌ها به‌طور خودکار به‌روزرسانی می‌شود.

## مقدار

یک {{domxref("HTMLCollection")}} زنده از اشیاء {{domxref("HTMLTableRowElement")}}.

## مثال‌ها

در این مثال، دو دکمه به شما امکان می‌دهند ردیف‌هایی را به بخش بدنه جدول اضافه یا از آن حذف کنید؛ همچنین یک عنصر {{HTMLElement("output")}} با تعداد ردیف‌های فعلی جدول به‌روزرسانی می‌شود.

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

### نتیجه

{{EmbedLiveSample("Examples", "100%", 175)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{cssxref("text-align")}}