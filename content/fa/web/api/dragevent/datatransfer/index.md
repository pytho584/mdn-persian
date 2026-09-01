---
title: "DragEvent: dataTransfer property"
short-title: dataTransfer
slug: Web/API/DragEvent/dataTransfer
page-type: web-api-instance-property
browser-compat: api.DragEvent.dataTransfer
---

{{APIRef("HTML Drag and Drop API")}}

خاصیت فقط‑خواندنی **`DragEvent.dataTransfer`** داده‌های عملیات کشیدن و رها کردن (به صورت یک شیء {{domxref("DataTransfer")}}) را در خود نگه می‌دارد.

## مقدار

یک شیء {{domxref("DataTransfer")}} که حاوی {{domxref("DragEvent","داده‌های رویداد کشیدن", "", 1)}} است.

این خاصیت زمانی که رویداد با استفاده از سازنده ایجاد شود، می‌تواند `null` باشد. اما زمانی که رویداد توسط مرورگر ارسال می‌شود، هرگز `null` نیست.

## مثال‌ها

این مثال نحوه دسترسی به داده‌های کشیدن و رها کردن را درون کنترل‌کننده رویداد {{domxref("HTMLElement/dragend_event", "dragend")}} نشان می‌دهد.

```js
function processData(d) {
  // پردازش داده‌ها …
}

dragTarget.addEventListener("dragend", (ev) => {
  // فراخوانی پردازشگر داده‌های کشیدن و رها کردن
  if (ev.dataTransfer !== null) processData(ev.dataTransfer);
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}