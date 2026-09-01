---
title: "DataTransferItem: getAsFile() method"
---

---
title: "DataTransferItem: getAsFile() method"
short-title: getAsFile()
slug: Web/API/DataTransferItem/getAsFile
page-type: web-api-instance-method
browser-compat: api.DataTransferItem.getAsFile
---

{{APIRef("HTML Drag and Drop API")}}

اگر آیتم یک فایل باشد، متد **`DataTransferItem.getAsFile()`** شیء {{domxref("File")}} آیتم داده‌ی درگ را برمی‌گرداند. اگر آیتم فایل نباشد، این متد `null` برمی‌گرداند.

## سینتکس

```js-nolint
getAsFile()
```

### پارامترها

هیچ.

### مقدار بازگشتی

اگر آیتم داده‌ی درگ یک فایل باشد، یک شیء {{domxref("File")}} برگردانده می‌شود؛ در غیر این صورت `null` برگردانده می‌شود.

## مثال‌ها

این مثال استفاده از متد `getAsFile()` را در یک مدیریت‌کننده رویداد {{domxref("HTMLElement/drop_event", "drop")}} نشان می‌دهد.

```js
function dropHandler(ev) {
  console.log("Drop");
  ev.preventDefault();
  for (const item of ev.dataTransfer.items) {
    if (item.kind === "string" && item.type.match("^text/plain")) {
      // This item is the target node
      item.getAsString((s) => {
        ev.target.appendChild(document.getElementById(s));
      });
    } else if (item.kind === "string" && item.type.match("^text/html")) {
      // Drag data item is HTML
      console.log("… Drop: HTML");
    } else if (item.kind === "string" && item.type.match("^text/uri-list")) {
      // Drag data item is URI
      console.log("… Drop: URI");
    } else if (item.kind === "file" && item.type.match("^image/")) {
      // Drag data item is an image file
      const f = item.getAsFile();
      console.log("… Drop: File");
    }
  }
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("DataTransfer.files")}}