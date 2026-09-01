---
title: "DataTransferItemList: add() method"
short-title: add()
slug: Web/API/DataTransferItemList/add
page-type: web-api-instance-method
browser-compat: api.DataTransferItemList.add
---

{{APIRef("HTML Drag and Drop API")}}

متد **`DataTransferItemList.add()`** یک {{domxref("DataTransferItem")}} جدید با استفاده از داده‌های مشخص‌شده ایجاد می‌کند و آن را به فهرست داده‌ی کشیدن (drag data list) اضافه می‌کند. آیتم می‌تواند یک {{domxref("File")}} یا یک رشته با نوع مشخص‌شده باشد. اگر آیتم با موفقیت به فهرست اضافه شود، شیء {{domxref("DataTransferItem")}} تازه‌ساخته بازگردانده می‌شود.

## Syntax

```js-nolint
add(data, type)
add(file)
```

### Parameters

- `data`
  - : رشته‌ای که داده‌های آیتم کشیدن را نشان می‌دهد.
- `type`
  - : رشته‌ای که نوع آیتم کشیدن را مشخص می‌کند. چند نمونه نوع عبارت‌اند از
    `text/html` و `text/plain`.
- `file`
  - : یک شیء {{domxref("File")}}. در این حالت نیازی به ارائه‌ی type نیست.

### Return value

یک {{domxref("DataTransferItem")}} که شامل داده‌های مشخص‌شده است. اگر آیتم کشیدن نتواند ساخته شود (مثلاً اگر شیء {{domxref("DataTransfer")}} مرتبط هیچ مخزن داده‌ای نداشته باشد)، `null` بازگردانده می‌شود.

### Exceptions

- `NotSupportedError` {{domxref("DOMException")}}
  - : اگر پارامتر رشته‌ای `data` ارائه شده باشد و فهرست از قبل شامل آیتمی باشد که {{domxref("DataTransferItem.kind","kind")}} آن `"Plain Unicode string"` است و نوع آن با پارامتر type مشخص‌شده یکسان باشد، پرتاب می‌شود.

## Examples

این مثال کاربرد متد `add()` را نشان می‌دهد.

### HTML

```html
<div>
  <p id="source" draggable="true">
    Select this element, drag it to the Drop Zone and then release the selection
    to move the element.
  </p>
</div>
<div id="target">Drop Zone</div>
```

### CSS

```css
div {
  margin: 0em;
  padding: 2em;
}
#source {
  color: blue;
  border: 1px solid black;
}
#target {
  border: 1px solid black;
}
```

### JavaScript

```js
const source = document.getElementById("source");
const target = document.getElementById("target");

source.addEventListener("dragstart", (ev) => {
  console.log("dragStart");
  // Add this element's id to the drag payload so the drop handler will
  // know which element to add to its tree
  const dataList = ev.dataTransfer.items;
  dataList.add(ev.target.id, "text/plain");
  // Add some other items to the drag payload
  dataList.add("<p>Paragraph…</p>", "text/html");
  dataList.add("http://www.example.org", "text/uri-list");
});

source.addEventListener("dragend", (ev) => {
  console.log("dragEnd");
  const dataList = ev.dataTransfer.items;
  for (let i = 0; i < dataList.length; i++) {
    dataList.remove(i);
  }
  // Clear any remaining drag data
  dataList.clear();
});

target.addEventListener("drop", (ev) => {
  console.log("Drop");
  ev.preventDefault();
  // Loop through the dropped items and log their data
  for (const item of event.dataTransfer.items) {
    if (item.kind === "string" && item.type.match("^text/plain")) {
      // This item is the target node
      item.getAsString((s) => {
        ev.target.appendChild(document.getElementById(s));
      });
    } else if (item.kind === "string" && item.type.match("^text/html")) {
      // Drag data item is HTML
      item.getAsString((s) => {
        console.log(`… Drop: HTML = ${s}`);
      });
    } else if (item.kind === "string" && item.type.match("^text/uri-list")) {
      // Drag data item is URI
      item.getAsString((s) => {
        console.log(`… Drop: URI = ${s}`);
      });
    }
  }
});

target.addEventListener("dragover", (ev) => {
  console.log("dragOver");
  ev.preventDefault();
  // Set the dropEffect to move
  ev.dataTransfer.dropEffect = "move";
});
```

### Result

{{EmbedLiveSample('Examples', 400, 300)}}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}