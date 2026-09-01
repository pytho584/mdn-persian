---
title: "DataTransferItemList: length property"
short-title: length
slug: Web/API/DataTransferItemList/length
page-type: web-api-instance-property
browser-compat: api.DataTransferItemList.length
---

{{APIRef("HTML Drag and Drop API")}}

ویژگی فقط‑خواندنی **`length`** از رابط {{domxref("DataTransferItemList")}} تعداد آیتم‌های موجود در لیست آیتم‌های کشیدن (drag) را برمی‌گرداند.

## مقدار

تعداد آیتم‌های داده‌ی کشیدن (drag data items) در لیست، یا 0 اگر لیست خالی یا غیرفعال باشد. لیست آیتم‌های کشیدن زمانی غیرفعال در نظر گرفته می‌شود که شیء {{domxref("DataTransfer")}} لیست آیتم با یک ذخیره‌گاه داده‌ی کشیدن (drag data store) مرتبط نباشد.

## مثال‌ها

این مثال استفاده از ویژگی `length` را نشان می‌دهد.

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
  const data = ev.dataTransfer.items;
  // Loop through the dropped items and log their data
  for (let i = 0; i < data.length; i++) {
    if (data[i].kind === "string" && data[i].type.match("^text/plain")) {
      // This item is the target node
      data[i].getAsString((s) => {
        ev.target.appendChild(document.getElementById(s));
      });
    } else if (data[i].kind === "string" && data[i].type.match("^text/html")) {
      // Drag data item is HTML
      data[i].getAsString((s) => {
        console.log(`… Drop: HTML = ${s}`);
      });
    } else if (
      data[i].kind === "string" &&
      data[i].type.match("^text/uri-list")
    ) {
      // Drag data item is URI
      data[i].getAsString((s) => {
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

### نتیجه

{{EmbedLiveSample('Examples', 100, 250)}}

## مشخصات‌نامه‌ها

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}