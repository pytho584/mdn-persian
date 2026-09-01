---
title: "DataTransferItem: type property"
---

---
title: "DataTransferItem: type property"
short-title: type
slug: Web/API/DataTransferItem/type
page-type: web-api-instance-property
browser-compat: api.DataTransferItem.type
---

{{APIRef("HTML Drag and Drop API")}}

ویژگی فقط‌خواندنی **`DataTransferItem.type`** نوع (فرمت) شیء {{domxref("DataTransferItem")}} را که نمایان‌گر آیتم دادهٔ کشیدن است، برمی‌گرداند. `type` یک رشتهٔ یونیکد است که معمولاً توسط یک نوع MIME داده می‌شود، هرچند که یک نوع MIME الزامی نیست.

برخی از انواع نمونه عبارتند از: `text/plain` و `text/html`.

## Value

رشته‌ای که نوع آیتم دادهٔ کشیدن را نشان می‌دهد.

## Examples

این مثال استفاده از ویژگی `type` را نشان می‌دهد.

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

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("DataTransfer.types()")}}
- [List of common MIME types](/en-US/docs/Web/HTTP/Guides/MIME_types/Common_types)