```
---
title: DataTransferItemList
slug: Web/API/DataTransferItemList
page-type: web-api-interface
browser-compat: api.DataTransferItemList
---

{{APIRef("HTML Drag and Drop API")}}

شیء **`DataTransferItemList`** فهرستی از اشیاء {{domxref("DataTransferItem")}} است که آیتم‌های در حال کشیده‌شدن را نمایش می‌دهد. در طی یک _عملیات کشیدن_، هر {{domxref("DragEvent")}} دارای یک ویژگی {{domxref("DragEvent.dataTransfer","dataTransfer")}} است و آن ویژگی یک `DataTransferItemList` است.

آیتم‌های جداگانه را می‌توان با استفاده از [نشانه‌گذاری براکت](/en-US/docs/Web/JavaScript/Reference/Operators/Property_accessors#bracket_notation) `[]` مورد دسترسی قرار داد.

`DataTransferItemList` در اصل برای [API کشیدن و رها کردن HTML](/en-US/docs/Web/API/HTML_Drag_and_Drop_API) طراحی شده بود و همچنان در بخش کشیدن و رها کردنِ HTML مشخص شده است، اما اکنون توسط سایر APIها مانند {{domxref("ClipboardEvent.clipboardData")}} و {{domxref("InputEvent.dataTransfer")}} نیز استفاده می‌شود. مستندات `DataTransferItemList` عمدتاً کاربرد آن را در عملیات کشیدن و رها کردن بررسی می‌کند و برای کاربرد `DataTransferItemList` در آن زمینه‌ها باید به مستندات سایر APIها مراجعه کنید.

این اینترفیس سازنده‌ای ندارد.

## ویژگی‌های نمونه

- {{domxref("DataTransferItemList.length")}} {{ReadOnlyInline}}
  - : یک `unsigned long` که تعداد آیتم‌های drag در فهرست است.

## متدهای نمونه

- {{domxref("DataTransferItemList.add()")}}
  - : یک آیتم (یا یک شیء {{domxref("File")}} یا یک رشته) را به فهرست آیتم‌های drag اضافه می‌کند و یک شیء {{domxref("DataTransferItem")}} برای آیتم جدید برمی‌گرداند.
- {{domxref("DataTransferItemList.remove()")}}
  - : آیتم drag را با شاخص داده‌شده از فهرست حذف می‌کند.
- {{domxref("DataTransferItemList.clear()")}}
  - : همه آیتم‌های drag را از فهرست حذف می‌کند.

## مثال

این مثال نحوه استفاده از کشیدن و رها کردن را نشان می‌دهد.

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

### نتیجه

{{EmbedLiveSample('Example', '35%', '250px')}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
```