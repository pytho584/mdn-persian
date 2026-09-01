---
title: "DataTransferItem: kind property"
short-title: kind
slug: Web/API/DataTransferItem/kind
page-type: web-api-instance-property
browser-compat: api.DataTransferItem.kind
---

{{APIRef("HTML Drag and Drop API")}}

ویژگی فقط خواندنی **`DataTransferItem.kind`** نوع — یک رشته یا یک فایل — از شیء {{domxref("DataTransferItem")}} را که نمایانگر _مورد داده‌ی کشیدن_ است، بازمی‌گرداند.

## مقدار

یک رشته که نوع مورد داده‌ی کشیدن را نشان می‌دهد. باید یکی از مقادیر زیر باشد:

- `'file'`
  - : اگر مورد داده‌ی کشیدن یک فایل باشد.
- `'string'`
  - : اگر نوع مورد داده‌ی کشیدن یک _رشته‌ی ساده‌ی یونیکد_ باشد.

## مثال‌ها

این مثال استفاده از ویژگی `kind` را نشان می‌دهد.

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

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [کشیدن و رها کردن](/en-US/docs/Web/API/HTML_Drag_and_Drop_API)
- [عملیات‌های کشیدن](/en-US/docs/Web/API/HTML_Drag_and_Drop_API/Drag_operations)
- [کار با ذخیره‌گاه داده‌ی کشیدن](/en-US/docs/Web/API/HTML_Drag_and_Drop_API/Drag_data_store)