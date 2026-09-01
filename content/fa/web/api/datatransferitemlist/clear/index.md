---
title: "DataTransferItemList: clear() method"
short-title: clear()
slug: Web/API/DataTransferItemList/clear
page-type: web-api-instance-method
browser-compat: api.DataTransferItemList.clear
---

{{APIRef("HTML Drag and Drop API")}}

متد **`clear()`** از {{domxref("DataTransferItemList")}} همهٔ اشیاء {{domxref("DataTransferItem")}} را از فهرست داده‌های کشیدن (drag data items list) حذف کرده و فهرست را خالی می‌کند.

ذخیره‌گاه داده‌های کشیدن (drag data store) که این فهرست در آن نگهداری می‌شود فقط در هنگام پردازش رویداد {{domxref("HTMLElement/dragstart_event", "dragstart")}} قابل نوشتن است. در هنگام پردازش {{domxref("HTMLElement/drop_event", "drop")}}، ذخیره‌گاه داده‌های کشیدن در حالت فقط‌خواندنی قرار دارد و این متد بی‌صدا هیچ کاری انجام نمی‌دهد. هیچ استثنایی پرتاب نمی‌شود.

## Syntax

```js-nolint
clear()
```

### Parameters

هیچکدام.

### Return value

هیچکدام ({{jsxref("undefined")}}).

## Examples

این مثال استفاده از متد `clear()` را نشان می‌دهد.

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

  // Clear any remaining drag data
  dataList.clear();
});

target.addEventListener("drop", (ev) => {
  console.log("Drop");
  ev.preventDefault();

  // Loop through the dropped items and log their data
  for (const item of ev.dataTransfer.items) {
    if (item.kind === "string" && item.type.match(/^text\/plain/)) {
      // This item is the target node
      item.getAsString((s) => {
        ev.target.appendChild(document.getElementById(s));
      });
    } else if (item.kind === "string" && item.type.match(/^text\/html/)) {
      // Drag data item is HTML
      item.getAsString((s) => {
        console.log(`… Drop: HTML = ${s}`);
      });
    } else if (item.kind === "string" && item.type.match(/^text\/uri-list/)) {
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