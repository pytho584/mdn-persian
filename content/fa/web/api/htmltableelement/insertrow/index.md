---
title: "HTMLTableElement: insertRow() method"
short-title: insertRow()
slug: Web/API/HTMLTableElement/insertRow
page-type: web-api-instance-method
browser-compat: api.HTMLTableElement.insertRow
---

{{APIRef("HTML DOM")}}

متد **`insertRow()`** از رابط {{domxref("HTMLTableElement")}} یک ردیف جدید ({{HtmlElement("tr")}}) را در یک {{HtmlElement("table")}} درج می‌کند و ارجاعی به ردیف جدید بازمی‌گرداند.

اگر یک جدول چند عنصر {{HtmlElement("tbody")}} داشته باشد، به‌طور پیش‌فرض ردیف جدید در آخرین `<tbody>` درج می‌شود. برای درج ردیف در یک بخش خاص، از {{domxref("HTMLTableSectionElement.insertRow()")}} استفاده کنید.

> **نکته:** `insertRow()` ردیف را مستقیماً در جدول درج می‌کند. نیازی به افزودن جداگانهٔ ردیف نیست؛ برخلاف حالتی که برای ایجاد عنصر `<tr>` جدید از {{domxref("Document.createElement()")}} استفاده شده باشد.

## Syntax

```js-nolint
insertRow()
insertRow(index)
```

{{domxref("HTMLTableElement")}} ارجاعی به یک عنصر HTML {{HtmlElement("table")}} است.

### Parameters

- `index` {{optional_inline}}
  - : شاخص (ایندکس) ردیف جدید. اگر `index` برابر با `-1` یا برابر با تعداد ردیف‌ها باشد، ردیف به‌عنوان آخرین ردیف اضافه می‌شود. اگر `index` حذف شود، مقدار پیش‌فرض آن `-1` است.

### Return value

یک {{domxref("HTMLTableRowElement")}} که ارجاعی به ردیف جدید است.

### Exceptions

- `IndexSizeError` {{domxref("DOMException")}}
  - : اگر `index` بزرگ‌تر از تعداد ردیف‌ها باشد پرتاب می‌شود.

## Examples

این مثال از `insertRow(-1)` برای افزودن یک ردیف جدید به جدول استفاده می‌کند.

سپس از {{domxref("HTMLTableRowElement.insertCell()")}} برای درج یک خانه (سلول) جدید در ردیف جدید استفاده می‌کنیم. (برای اینکه HTML معتبر باشد، یک `<tr>` باید حداقل یک عنصر `<td>` داشته باشد.) در پایان، با استفاده از {{domxref("Document.createTextNode()")}} و {{domxref("Node.appendChild()")}} متنی به خانه اضافه می‌کنیم.

### HTML

```html
<table id="my-table">
  <tbody>
    <tr>
      <td>Row 1</td>
    </tr>
    <tr>
      <td>Row 2</td>
    </tr>
    <tr>
      <td>Row 3</td>
    </tr>
  </tbody>
</table>
```

### JavaScript

```js
function addRow(tableID) {
  // Get a reference to the table
  let tableRef = document.getElementById(tableID);

  // Insert a row at the end of the table
  let newRow = tableRef.insertRow(-1);

  // Insert a cell in the row at index 0
  let newCell = newRow.insertCell(0);

  // Append a text node to the cell
  let newText = document.createTextNode("New bottom row");
  newCell.appendChild(newText);
}

// Call addRow() with the table's ID
addRow("my-table");
```

### Result

{{EmbedLiveSample("Examples")}}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("HTMLTableRowElement.insertCell()")}}
- {{domxref("HTMLTableSectionElement.insertRow()")}}