---
title: "DataTransferItem: getAsString() method"
---

---
title: "DataTransferItem: getAsString() method"
short-title: getAsString()
slug: Web/API/DataTransferItem/getAsString
page-type: web-api-instance-method
browser-compat: api.DataTransferItem.getAsString
---

{{APIRef("HTML Drag and Drop API")}}

متد **`DataTransferItem.getAsString()`**، زمانی که {{domxref("DataTransferItem.kind","kind")}} آیتم یک _رشته‌ی ساده‌ی یونیکد_ است (یعنی `kind` برابر با `string`)، تابع بازخوانی داده‌شده را با داده رشته‌ای آیتم داده درگ به‌عنوان آرگومان فراخوانی می‌کند.

## نحو

```js-nolint
getAsString(callbackFn)
```

### پارامترها

- `callbackFn`
  - : تابع بازخوانی که آرگومان‌های زیر را دریافت می‌کند:
    - `data`
      - : داده رشته‌ای {{domxref("DataTransferItem")}}.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

این مثال استفاده از متد `getAsString()` را به‌عنوان یک _تابع درون‌خطی_ در یک مدیریت‌کننده رویداد {{domxref("HTMLElement/drop_event", "drop")}} نشان می‌دهد.

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

- {{domxref("DataTransfer.getData()")}}